<template>
  <div id="app">
    <h1>Aaaaaaaaaaaaaaaaaaaaaaaaaa</h1>
    <hr>
    <router-view />
  </div>
</template>

<script>
import TodoList from '@/components/TodoList';
import AddTodoComponent from '@/components/AddTodoComponent'

export default {
  name: 'App',
  data() {
    return{
      todos: [
        {id: 1, title: 'Купить чашку', completed: false},
        {id: 2, title: 'Купить кадди', completed: false},
        {id: 3, title: 'Купить заглушку', completed: false}
      ]
    }
  },
  mounted() {
    fetch('https://jsonplaceholder.typicode.com/todos?_limit=3')
      .then(response => response.json())
      .then(json => {
        this.todos = json
      })
  },
  methods: {
    removeTodo(id) {
      this.todos = this.todos.filter((todo) => todo.id !== id)
    },
    addTodo (todo) {
      this.todos.push(todo);
    }
  },
  components: {
    TodoList, AddTodoComponent
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
