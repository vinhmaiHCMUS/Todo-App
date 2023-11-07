<template>
  <div>
    <h1>Todo App</h1>
    <input
      type="text"
      v-model="newTodo"
      @keyup.enter="addTodo"
      placeholder="Add a new task"
    />

    <ul>
      <li v-for="(todo, index) in todos" :key="index">
        <input
          type="checkbox"
          v-model="todo.completed"
        />
        <span :class="{ completed: todo.completed }">{{ todo.text }}</span>
        <button @click="removeTodo(index)">Delete</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTodo: '',
      todos: []
    };
  },
  methods: {
    addTodo() {
      if (this.newTodo.trim() === '') return;
      this.todos.push({ text: this.newTodo, completed: false });
      this.newTodo = '';
    },
    removeTodo(index) {
      this.todos.splice(index, 1);
    }
  }
};
</script>

<style>
.completed {
  text-decoration: line-through;
}
</style>
