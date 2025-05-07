<template>
  <main class="p-8">
    <h1 class="text-3xl font-bold mb-4">Blog Terbaru</h1>
    <div v-for="article in articles" :key="article._path" class="mb-4">
      <NuxtLink :to="article._path" class="text-xl text-blue-600 hover:underline">
        {{ article.title }}
      </NuxtLink>
      <p class="text-gray-500">{{ article.description }}</p>
    </div>
  </main>
</template>

<script setup>
const { data: articles } = await useAsyncData('articles', () =>
  queryContent().only(['_path', 'title', 'description']).find()
)
</script>
