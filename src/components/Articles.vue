<template>
  <div class="section">
    <ul class="article-list">
    <marquee scrollamount="50">
        <img :src="`${$static.header.edges[0].node.mainImage.file.url.src}`">
    </marquee>
    <h1>The many faces of Sylvester Stallone</h1>
    <marquee scrollamount="10" direction="up">
      <img :src="`${$static.header.edges[1].node.mainImage.file.url.src}`">
    </marquee>
    <marquee scrollamount="50" direction="right">
      <img :src="`${$static.header.edges[2].node.mainImage.file.url.src}`">
    </marquee>
    </ul>
  </div>
</template>
<static-query>
  query HomeQuery {
    posts: allContentfulBlogPost {
      edges {
        node {
          title
          description
          slug
          publishDate(format: "MMMM Do, YYYY")
          tags
          heroImage {
            path
            slug
            file {
              fileName
              url
            }
          }
          description
        }
      }
    }
    header: 
  allContentfulPageHeader {
    edges {
      node {
        title
        subHeading
        mainImage {
          path
          slug
          file {
            url
            fileName
          }
        }
        
      }
    }
  }
}

</static-query>
<script>

export default {
  components: {
  },
};
</script>

<style scoped>
  .section {
    display: flex;
    align-items: center;
    height: 500px;
  }
  ul {
    height: 100%; 
    display: flex;
    align-items: center;
  }

  h1 {
    font-weight: bold;
    width: 300px;
    height: 100px;
    animation-name: spin;
    animation-duration: 5000ms;
    animation-iteration-count: infinite;
    animation-timing-function: linear; 
  }

@keyframes spin {
    from {
        transform:rotate(0deg);
    }
    to {
        transform:rotate(360deg);
    }
}
</style>
