<template>
  <div id="app">
    <button type="button" @click="geta()">보기</button>
  
      <h2>?? : {{ name }}</h2>
    
  </div>
</template>

<script>
import axios from "axios"
export default {

  data() {
    return {
    
      lol: {},
      name: ''

    }
  },
  methods: {
    geta :function() {
      const BASE_URL = 'https://cors.io/?https://kr.api.riotgames.com/lol/summoner/v4/summoners/by-name/yamine?api_key=RGAPI-5bfa2b4b-0bbf-4861-a97a-dfd697046e26'
      const headers = {
        "Origin": "https://developer.riotgames.com",
                "Accept-Charset": "application/x-www-form-urlencoded; charset=UTF-8",
                "X-Riot-Token": "RGAPI-5bfa2b4b-0bbf-4861-a97a-dfd697046e26",
                "Accept-Language": "ko-KR,ko;q=0.9,en-US;q=0.8,en;q=0.7",
                "User-Agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/79.0.3945.117 Safari/537.36",
                "Access-Control-Allow-Origin": "true",
                'Content-Type': 'application/json'
              }

      axios({
        method: 'get',
        url : `${BASE_URL}`,
        headers: `${headers}`,
        mode: 'cors'
      })
      .then(res=>{
        alert(res.data)
        this.name = res.data['yamine']
        
      })
      .catch(e=>{
        alert('실패'+e)
      })
            
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>