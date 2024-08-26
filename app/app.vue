<script lang="ts" setup>
const open = ref(false);
const location = [6.207, 7.067];
</script>
<template>
  <div>
    <NuxtRouteAnnouncer />
    <div class="container mx-auto p-16">
      <h1>Hello world!</h1>
      <UButton @click="open = true">Open</UButton>
      <div class="h-[350px] isolate">
        <LMap :zoom="6" :center="location" :use-global-leaflet="false">
          <LTileLayer
            url="https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png"
            attribution='&amp;copy; <a href="https://www.openstreetmap.org/">OpenStreetMap</a> contributors'
            layer-type="base"
            name="OpenStreetMap"
          />

          <LMarker :lat-lng="location" draggable />
          <LCircle :lat-lng="location" :radius="50000" />
        </LMap>
      </div>

      <UModal v-model="open">
        <UCard>
          <template #header> Map Test </template>

          <!-- <ClientOnly> -->
          <div style="height: 350px">
            <LMap
              class="h-full"
              :zoom="6"
              :center="location"
              :use-global-leaflet="false"
            >
              <LTileLayer
                url="https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png"
                attribution='&amp;copy; <a href="https://www.openstreetmap.org/">OpenStreetMap</a> contributors'
                layer-type="base"
                name="OpenStreetMap"
              />
              <LMarker :lat-lng="location" draggable />
              <LCircle :lat-lng="location" :radius="50000" />
            </LMap>
          </div>
          <!-- </ClientOnly> -->
        </UCard>
      </UModal>
    </div>
  </div>
</template>
