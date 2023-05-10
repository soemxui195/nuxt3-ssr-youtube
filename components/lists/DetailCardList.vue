<template>
  <!-- https://tailwindcomponents.com/component/youtube-home-timeline -->
  <div class="flex justify-center p-5 bg-[#181818]">
    <div class="grid max-w-6xl grid-cols-12 gap-2 gap-y-4">
      <div v-for="product in products" :key="product.id" class="col-span-12 sm:col-span-6 md:col-span-3">
        <div class="flex flex-col w-full">
          <div class="relative">
            <!-- Image Video -->
            <a href="/explore">
              <img :src="product.images[0]" class="h-auto w-96" />
            </a>

            <p class="absolute px-1 text-xs text-gray-100 bg-gray-900 right-2 bottom-2 py">1:15</p>
          </div>

          <div class="flex flex-row gap-2 mt-2">
            <!-- Profile Picture -->
            <a href="/explore">
              <img :src="product.category.images" class="h-auto w-rounded-full max-h-10 max-w-10" />
            </a>

            <!-- Description -->
            <div clas="flex flex-col">
              <a href="/explore">
                <p class="text-sm font-semibold text-gray-100" v-text="product.title"></p>
              </a>
              <a class="mt-2 text-xs text-gray-400 hover:text-gray-100" href="#"> Leon To </a>
              <p class="mt-1 text-xs text-gray-400">241K views . 3 years ago</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
const { data: products } = await useAsyncData('product', () =>
  $fetch(`https://api.escuelajs.co/api/v1/products?offset=10&limit=8`, {
    method: 'GET',
  })
);
</script>
