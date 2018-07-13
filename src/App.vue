<template>
  <div class="container">
   <div class="content" v-for="article in news">
    <img :src="article.urlToImage" alt="">
    <h3>
      {{article.title}}
    </h3>
    <h4>
      {{article.author}}
    </h4>
    <blockquote>
    <p>{{article.description}}</p>

    </blockquote>
    <a href="#" target="blank" class="button">Read More</a>
  </div>


  </div>
</template>

<script>

const url = "https://newsapi.org/v2/top-headlines?country=us&category=business&apiKey=631a7de19d75427ea6afea262d7e9f6b";
import axios from 'axios'

const data = {
  news:[]
}


export default {
  data: function() {
    return data 
  },
  created(){
  this.loadNews();
  },
  methods: {
  	   loadNews(){
      axios.get(url).then(function(response) {
        console.log(response.data.articles)
        data.news = (response.data.articles)
     }).catch(function(error) {
        console.log(error.message)
    })
   }
  }

}
</script>
