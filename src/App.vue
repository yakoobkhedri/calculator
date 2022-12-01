<template>
<body>
    <div class="container">
        <div class="calculator">
            <input type="text" class="input" v-model="currentNumber">
            <div class="buttons">
                <div>
                    <button class="btn ac" @click="clear">AC</button>
                    <button class="btn">DEL</button>
                    <button class="btn num sign" @click="operate('%')">%</button>
                    <button class="btn num sign" @click="operate('/')">/</button>
                </div>
                <div>
                    <button class="btn num" @click="addNumber('7')">7</button>
                    <button class="btn num" @click="addNumber('8')">8</button>
                    <button class="btn num" @click="addNumber('9')">9</button>
                    <button class="btn num sign" @click="operate('*')">*</button>
                </div>
                <div>
                    <button class="btn num" @click="addNumber('4')">4</button>
                    <button class="btn num" @click="addNumber('5')">5</button>
                    <button class="btn num" @click="addNumber('6')">6</button>
                    <button class="btn num sign" @click="operate('-')">-</button>
                </div>
                <div>
                    <button class="btn num" @click="addNumber('1')">1</button>
                    <button class="btn num" @click="addNumber('2')">2</button>
                    <button class="btn num" @click="addNumber('3')">3</button>
                    <button class="btn num sign" @click="operate('+')">+</button>
                </div>
                <div>
                    <button class="btn num" @click="addNumber('0')">0</button>
                    <button class="btn num sign" @click="addDot">.</button>
                    <button class="btn equal sign" @click="equal">=</button>
                </div>
            </div>
        </div>
    </div>
</body>

</template>

<script>

export default {
  name: 'App',
  data() {
    return {
    currentNumber:'',
    prevNumber:'',
    operation:''
    }
  },
  methods: {
    addNumber(number){
      if(this.currentNumber==0&&number==0) return;
      this.currentNumber+=number
    },
    addDot(){
      if(this.currentNumber.includes('.')) return;
      this.currentNumber+='.';
    },
    clear(){
      this.currentNumber=''
    },
    operate(operation){
      this.prevNumber=this.currentNumber;
      this.currentNumber='';
      this.operation=operation
    },
    equal(){
      switch (this.operation) {
        case '+':
          this.currentNumber=parseFloat(this.prevNumber)+parseFloat(this.currentNumber);
          break;
        case '-':
          this.currentNumber=parseFloat(this.prevNumber)-parseFloat(this.currentNumber);
          break;
        case '*':
          this.currentNumber=parseFloat(this.prevNumber)*parseFloat(this.currentNumber);
          break;
        case '/':
          this.currentNumber=parseFloat(this.prevNumber)/parseFloat(this.currentNumber);
          break;
        case '%':
          this.currentNumber=parseFloat(this.prevNumber)%parseFloat(this.currentNumber);
          break;
      }
        this.currentNumber=this.currentNumber.toString()
    }
  },
  }
</script>

<style lang="sass">

</style>
