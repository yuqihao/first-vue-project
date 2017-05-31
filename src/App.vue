<template>
  <div id="app">
    <!-- <img src="./assets/logo.png">
    <router-view></router-view> -->

    <h1 v-text="title"></h1>
    <input v-model="newItem" v-on:keyup.enter="addNew">
    <ul>
      <li v-for="item in items" v-bind:class="{finished:item.isFinished}" v-on:click="toggleFinish(item)">
        {{item.label}}
      </li>
    </ul>

  </div>
</template>

<script>
export default {
  // name: 'app'
   data () {
    return {
     title: 'this is a todo list',
     items: [
        {
          label:'coding',
          isFinished:false
        },
        {
          label:'walking',
          isFinished:true
        }

     ],
     newItem:'',
    }
  },
  methods:{
    toggleFinish:function (item) {
      item.isFinished=!item.isFinished
    },
    addNew:function(item){
      this.items.push({
        label:this.newItem,
        isFinished:false,
      })
      this.newItem=''
    }
  }

}
</script>




<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 160px;
}

ul{
  position: relative;
  margin: 0 auto;
  width: 200px;
}

.finished{
  text-decoration: underline;
}
</style>
