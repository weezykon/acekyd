<template>
  <Layout :show-logo="false">
    <!-- Author intro -->
    <Header :show-title="true" />

    <!-- List posts -->
    <div class="posts">
      <PostCard v-for="edge in $page.posts.edges" :key="edge.node.id" :post="edge.node"/>
    </div>

  </Layout>
</template>

<page-query>
query {
  posts: allPost(filter: { published: { eq: true }}) {
    edges {
      node {
        id
        title
        date (format: "D. MMMM YYYY")
        timeToRead
        description
        cover_image (width: 770, height: 380, blur: 10)
        path
        tags {
          id
          title
          path
        }
      }
    }
  }
}
</page-query>

<script>
import Header from '~/components/Header.vue'
import PostCard from '~/components/PostCard.vue'

export default {
  components: {
    Header,
    PostCard
  },
  metaInfo: {
    title: 'Adewale Abati',
    meta: [
      {
        key: 'og:title',
        property: 'og:title',
        content: 'Adewale Abati - Blog!',
      }
    ]
  }
}
</script>
