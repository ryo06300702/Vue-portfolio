<template>
  <div id="App">
    <input type="text" v-model="text">
    <p :class="{bibit: stringLength > 20}">現在{{ stringLength }}文字です</p>
    <button @click="alert" :disabled="overLength">送信</button>
    <p v-if="overLength" class="bibit">条件を満たしていません</p>
    <p v-if="showFlg">どーーーーーーーーーーーーんっ！！！</p>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      text: '',
      showFlg: false,
    }
  },
  computed: {
    stringLength() {
      return this.text.length;
    },
    overLength() {
      return this.text.length > 20 || 0 == this.text.length;
    },
  },
  methods: {
    alert() {
      if (this.overLength)
      {
        alert("Fuck You!!");
      } else {
        confirm("WoW");
        const answer = confirm();
        this.show(answer);
      }
    },
    show(answer) {
      if(answer) {
        this.showFlg = true;
      }
    },
  },
}
</script>

<style>
#App {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
 .bibit {
  color: red;
  text-align: center;
 }
</style>
