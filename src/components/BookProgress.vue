<script setup>
import { computed } from "vue"

const props = defineProps(["books"])

const countBooksRead = computed(() => {
  return props.books.filter((book) => book.isRead).length
})

const booksReadMessage = computed(() => {
  return countBooksRead.value >= props.books.length
    ? "Parabéns, você leu todos os livros!"
    : `${countBooksRead.value} de ${props.books.length} livros lidos`
})
</script>
<template>
  <div class="books-read">
    <label for="progress">Seu Progresso</label>
    <br />
    <progress :value="countBooksRead" :max="books.length"></progress>
    <p>{{ booksReadMessage }}</p>
  </div>
</template>
