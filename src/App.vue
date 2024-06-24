<script setup>
import {ref} from "vue";

let id = 0;
const todos = ref([
]);

const newTodo = ref("");

const addTodo = () => {
  let todoObj = {
    id:id++,
    work:newTodo.value,
  };
  todos.value.push(todoObj);
};

const removeTodo = (todo) => {
  todos.value = todos.value.filter((td)=>td !== todo)
};
</script>

<template>
  <div class="container">
    <h1>Todo List</h1>
    <input v-model = "newTodo"/>
    <button @click="addTodo">Add</button><br><br>
    <h>Todo List : </h>
    <ul>
      <li v-for="todo in todos" :key="todo.id">
        <label>{{ todo.work }}</label>
        <button @click="removeTodo(todo)">X</button>
      </li>
    </ul>
  </div>
</template>

<style>
body, h1, ul, li, input, button {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: Arial, sans-serif;
  background-color: #f4f4f4;
  display: flex;
  justify-content: center;
  align-items: center;
}

.container {
  background: #fff;
  padding: 20px 30px;
  border-radius: 10px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  align-items: center;
}

h1 {
  text-align: center;
  margin-bottom: 20px;
}

.form {
  display: flex;
}

ul {
  list-style-type: none;
}

li {
  padding: 10px;
  border: 1px solid #ddd;
  margin-bottom: 10px;
  border-radius: 4px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

li label {
  flex: 1;
}

li button {
  border: none;
  color: #c9302c;
  padding: 10px;
  border-radius: 4px;
  cursor: pointer;
}

li button:hover {
  background: #c9302c;
  color: #ddd
}
</style>