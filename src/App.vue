<template>
  <div id="app">
    <h1>Bin2Dec</h1>
    <input id="input" type="text" v-model="bin" @keyup="change">
    <p v-if="result >= 0">Result: {{result}}</p>
  </div>
</template>

<script>
const regex = new RegExp("^[0-1]+$")

export default {
  name: "App",
  data() {
    return {
      bin: "",
      result: -1
    };
  },
  methods: {
    change() {
      if(!regex.test(this.bin) && this.bin.length > 0) {
        this.result = "Warning! Only 0 and 1 are allowed!";
        return;
      } else if(this.bin.length == 0) {
        this.result = -1;
      } else {
        this.result = 0
        for(let i = 0; i < this.bin.length; i++) {
          this.result += parseInt(this.bin[i]) * Math.pow(2, this.bin.length - i -1);
        }
      }
    }
  }
}
</script>

<style>
  * {
    font-family: sans-serif;
    text-align: center;
  }
</style>