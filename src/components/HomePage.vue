<template>
    <div>
      <div>
      <input v-model="mod" placeholder="MOD" />
      <input v-model="multiplier" placeholder="MULTIPLIER" />
      </div>        
        <input v-model="message" placeholder="Enter number" />
        <button @click="calculate">Calculate</button>
        <p>{{result}}</p>
    </div>
</template>

<script>
export default {
  name: 'HomePage',
  data() {
    return {
      message: "",
      result: "",
      mod: 97,
      multiplier: 10
    }
  },
  methods: {
    calculate(){
      let result = 0;
      for(let digit of this.message){
        let numDigit = parseInt(digit, 10);
        let temp = result + numDigit;
        result = (temp * this.multiplier) % this.mod;
      }
      result = (this.mod + 1 - result) % this.mod;
      this.result = result;
    }
  }
}
</script>