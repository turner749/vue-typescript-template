<template>
  <a-card
    hoverable
    :style="{
      width: '70vw',
      display: 'inline-flex',
      justifyContent: 'center',
    }"
  >
    <!--    <h1>{{ user.name.first }}</h1>-->
    <a :href="user.picture.large" target="_blank">
      <img alt="example" :src="user.picture.large" />
    </a>
    <template class="ant-card-actions">
      <!--      <a-icon key="setting" type="setting" />-->
      <!--      <a-icon key="edit" type="edit" />-->
      <!--      <a-icon key="ellipsis" type="ellipsis" />-->
    </template>
    <a-card-meta
      className="card-title"
      :title="user.name.first + ` ` + user.name.last"
      description=""
    >
      <!--      <a-avatar :src="user.picture.large" />-->
    </a-card-meta>
    <h5>Email: {{ user.email }}</h5>
    <h5>Phone: {{ user.phone }}</h5>
    <a-button @click="onDelete">Delete User</a-button>
  </a-card>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "UserCard",
  props: {
    user: Object,
  },
  emits: ["delete-user"],
  methods: {
    onDelete(e: any) {
      e.preventDefault();
      this.$emit("delete-user", this.user?.login.uuid);
    },
  },
});
</script>

<style scoped>
.card-title {
  padding-top: 7px;
}
</style>
