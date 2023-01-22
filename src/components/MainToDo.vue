<script setup>
import { ref } from 'vue';
const todoRef = ref('');
const todoListRef = ref([]);

const addToDo = () => {
  const id = new Date().getTime();
  todoListRef.value.push({ id: id, task: todoRef.value });
  localStorage.todoList = JSON.stringify(todoListRef);

  todoRef.value = '';
};
</script>

<template>
  <div class="box_input">
    <input type="text" class="todo_input" v-model="todoRef" placeholder="+ Todoを入力" />
    <button class="btn" @click="addToDo">登録するs</button>
  </div>
</template>

<style scoped>
.box_input {
  margin-top: 20px;
  width: 400px;
}

.todo_input {
  width: 300px;
  margin-right: 8px;
  padding: 8px;
  font-size: 18px;
  border: 1px solid #aaa;
  border-radius: 6px;
}

.btn {
  width: 50px;
  padding: 8px;
  background-color: #03a9f4;
  border-radius: 8px;
  color: #fff;
  text-align: center;
  font-size: 14px;
}
</style>
