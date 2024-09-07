<!-- js -->
<script setup>
import { ref } from 'vue';

const inputValue = ref('');
const todoList = ref([
  { text: 'vue', done: false },
  { text: 'react', done: false },
  { text: 'vercel', done: false },
]);

const initValue = {};

console.log(todoList.value);

const count = ref(0);

const increase = () => {
  count.value = count.value + 1;
};

const decrease = () => {
  count.value = count.value - 1;
};

const showValue = () => {
  const text = inputValue.value;

  todoList.value.push({
    text: text,
    don: false
  });
  console.log(todoList.value);
};

const handleChange = (event) => {
  console.log(event);

  const nextValue = event.target.value;
  inputValue.value = nextValue;
};

const handleClickDeleteButton = (index) => {
  todoList.value.splice(index, 1);
};
</script>

<!-- html -->
<template>
  <h3>TODO LIST</h3>

  <div>
    <div>count : {{ count }}</div>
    <button @click="increase">+</button>
    <button @click="decrease">-</button>
  </div>

  <input v-model="inputValue" />
  <!-- <input :model="inputValue"/> -->
  <!-- <input :value="inputValue" @change="handleChange" /> -->
  <p>{{ todoList }}</p>
  <button @click="showValue">확인</button>

  <div class="todo-item" v-for="(item, index) in todoList">
    <input type="checkbox" v-model="item.done" />
    <span :class="{ 'done-item': item.done }">{{ item.text }}</span>

    <button>수정</button>
    <button @click="handleClickDeleteButton(index)">삭제</button>
  </div>
</template>

<!-- Css -->

<style scoped>
h1 {
  color: purple;
}
.todo-item {
  width: 100%;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  border: 1px solid gray;
}

.done-item {
  text-decoration: line-through;
}
</style>
