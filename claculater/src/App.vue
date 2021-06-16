<template>
  <div class="container">
    <div class="result">
      <input type="text" v-model="number">
    </div>


    <div class="buttons">
      <div class="button action-btn" @click="clear"> C </div>
      <div class="button action-btn" @click="minesPlus"> +/-</div>
      <div class="button num-button  action-btn" @click="handleOpration('%')"> %</div>
      <div class="button num-button  calc-action-btn" @click="handleOpration('/')"> /</div>
      <div class="button num-button seven" @click="addNumber(7)">7</div>
      <div class="button num-button eight" @click="addNumber(8)">8</div>
      <div class="button num-button  nine" @click="addNumber(9)">9</div>
      <div class="button num-button  calc-action-btn" @click="handleOpration('*')">*</div>
      <div class="button num-button  four" @click="addNumber(4)">4</div>
      <div class="button num-button  five" @click="addNumber(5)">5</div>
      <div class="button num-button  six" @click="addNumber(6)">6</div>
      <div class="button num-button  calc-action-btn" @click="handleOpration('-')">-</div>
      <div class="button num-button  one" @click="addNumber(1)">1</div>
      <div class="button num-button  two" @click="addNumber(2)">2</div>
      <div class="button num-button  three" @click="addNumber(3)">3</div>
      <div class="button num-button  calc-action-btn" @click="handleOpration('+')">+</div>
      <div class="button num-button  zero" @click="addNumber(0)">0</div>
      <div class="button num-button  point" @click="addDot" >.</div>
      <div class="button calc-action-btn" @click="equal">=</div>
    </div>

  </div>
</template>

<script>
export default {
  name: 'App',
  data(){
    return{
      number:'',
      opration:'',
      prevNumber:'',
    }
  },

  methods:{
  
    addNumber(num){
      if( this.number == 0 && num ==0 ) return;
        this.number += num
    },

    addDot(){
      if(this.number.includes('.')) return;
      this.number += '.'
    },

    clear(){
      this.number='';
    },

    minesPlus(){
      if(parseFloat(this.number) >0 ){
        this.number = '-' + this.number
      } else {
        this.number = this.number.substring(1)
      }
    },

    handleOpration(opration){
      this.prevNumber = this.number;
      this.number = '';
      this.opration = opration;
    },

    equal(){
      switch(this.opration) {
        case '+' :
          this.number = parseFloat(this.prevNumber) + parseFloat(this.number);
          break;

        case '-' :
          this.number = parseFloat(this.prevNumber) - parseFloat(this.number);
          break;

        case '*' :
          this.number = parseFloat(this.prevNumber) * parseFloat(this.number);
          break;

        case '/' :
          this.number = parseFloat(this.prevNumber) / parseFloat(this.number);
          break;

        case '%' :
          this.number = parseFloat(this.prevNumber) % parseFloat(this.number);
          break;
      }
       this.number = this.number.toString();
    }
  }
  
}
</script>

<style lang="scss">

</style>
