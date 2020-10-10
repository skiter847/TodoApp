<template>
  <ul>
    <TodoItem v-for="(todo, index) in todos"
              :todo="todo"
              :key="index"
              @remove-todo="removeTodo(index)"
              @set-status="setStatus(index)"
    />
  </ul>
</template>

<script>
import TodoItem from "@/components/TodoItem";

export default {

  name: "TodoList",
  components: {
    TodoItem
  },
  props: {
    todos: Array,
  },

  methods: {
    removeTodo(index) {
      this.$emit('remove-todo', index)
    },
    setStatus(index) {
      this.$emit('set-status', index)
    }
  }
}
</script>

<style>
ul {
  max-height: 400px;
  width: 97%;
  overflow-y: scroll;
}

/* width */
::-webkit-scrollbar {
  width: 10px;
}

/* Track */
::-webkit-scrollbar-track {
  background: #f1f1f1;
}

/* Handle */
::-webkit-scrollbar-thumb {
  background: #4169E1;
}

/* Handle on hover */
::-webkit-scrollbar-thumb:hover {
  background: #555;
}
</style>