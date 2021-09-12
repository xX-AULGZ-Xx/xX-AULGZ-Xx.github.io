<template>
  <div>
    <nevbar></nevbar>
    <br>
    <b-container>
    <b-row>
      <b-col v-for="post in posts" :key="post.slug">
        <b-card
          :title="post.title"
          :img-src="post.image"
          img-alt="Image"
          img-top
          tag="article"
          style="max-width: 50rem"
          class="auto"
        >
          <b-card-text>
            {{post.description}}
          </b-card-text>

          <b-button :to="{name: 'posts-slug', params: {slug:post.slug}}" variant="primary">Read More!</b-button>
        </b-card>
      </b-col>
    </b-row>
    </b-container>



  </div>
</template>

<script>
import nevbar from '../components/nevbar.vue';
export default {
  components: { nevbar },
  async asyncData({ $content }) {
    const postsData = await $content('posts').fetch();
    return {
      posts: postsData,
    };
  },
  mounted() {
    console.log('THIS.POSTS', this.posts);
  },
};
</script>
