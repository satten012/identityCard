<template>  
    <div id="app"><button @click="btr">click me</button>
</div>
<div v-if="info" class= "informaton">
  <div class = "informatonIdentity">IDENTITY CARD</div>
  <div class = "informationPerson">  
      <div><img src="./assets/personalPhoto.jpeg" alt="photo"></div>
    <div class="informationPersonMain"><span> Main information </span>
      <div class = "informationPersonMainName"> <span> Name:  </span>{{info.data.name  }}</div>
      <div class = "informationPersonMainHeight"> <span> Height:  </span>{{info.data.height  }}</div>
      <div class = "informationPersonMainMass"> <span> Mass:  </span>{{info.data.mass  }}</div>
      <div class = "informationPersonMainHairColor"><span> Hair color:  </span>{{info.data.hair_color}}</div>
      <div class = "informationPersonMainSkinColor"> <span> Skin_color:</span>  {{info.data.skin_color}}</div>
      <div class = "informationPersonMainEyeColor"> <span> Eye_color:  </span>{{info.data.eye_color}}</div>
      <div class = "informationPersonMainBirthYear"><span> Birth year: </span> {{info.data.birth_year  }}</div>
      <div class = "informationPersonMainGender"> <span> Gender: </span>{{info.data.gender  }}</div>
    </div>  
    <div class="informationPersonHobby"><span> Hobbies </span> 
      <div class = "informationPersonHobbyHomeworld"><span> homeworld:</span><br>  {{info.data.homeworld  }}</div>
      <div class = "informationPersonHobbyFilms"><span> films: </span><br> {{info.data.films.join(", ")  }}</div>
      <div class = "informationPersonHobbySpecies"><span> species: </span> {{info.data.species.join(", ")  }}</div>
      <div class = "informationPersonHobbyStarships"><span> starships: </span> <br> {{info.data.starships.join(", ")  }}</div>
      <div class = "informationPersonHobbyCreated"><span> created: </span><br> {{info.data.created  }}</div>
      <div class = "informationPersonHobbyEdited"><span> edited: </span><br> {{info.data.edited  }}</div>
      <div class = "informationPersonHobbyUrl"><span> url: </span><br> {{info.data.url  }}</div>
    </div>
  </div>
</div>

</template>

<script>
  export default {
    el: '#app',
  data () {
    return {
      info: null
    }
  },
  methods:{
    btr(){
      axios
      .get('https://swapi.dev/api/people/1/')
      .then(response => (this.info = response)) 
    }
  }
  }
</script>

<style>
  * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
  }
  button{
    padding: 15px;
    border-radius: 50%;
    background-color: #23d5ab;
    border: 1px dotted #000;
  }

  #app > button:hover{
    background-color: #e73c7e;
  }

  img{
    width: 250px;
    height: 330px;
    border-radius: 40px;
    margin: 15px 55px 0px 15px;
    -webkit-box-shadow: 5px 5px 0px 0px #289FED, 10px 10px 0px 0px #5FB8FF, 15px 15px 0px 0px #A1D8FF, 20px 20px 0px 0px #CAE6FF, 25px 25px 0px 0px #E1EEFF, 5px 5px 15px 5px rgba(0,0,0,0); 
    box-shadow: 5px 5px 0px 0px #289FED, 10px 10px 0px 0px #5FB8FF, 15px 15px 0px 0px #A1D8FF, 20px 20px 0px 0px #CAE6FF, 25px 25px 0px 0px #E1EEFF, 5px 5px 15px 5px rgba(0,0,0,0);
  }
  .informationPerson{
    display: flex;
  }
  .informaton{
    border: 2px solid #000;
    background: linear-gradient(-45deg, #ee7752, #e73c7e, #23a6d5, #23d5ab);
	  animation: gradient 15s ease infinite;
    width: max-content;
    border-radius: 25px;
    margin: auto;
  }
  
  .informatonIdentity{
    border-bottom: 2px solid #000;
    text-align: center;
    font-size: 28px;
    font-weight: 900;
  }

  .informationPersonMain, .informationPersonHobby {
    margin-top:15px;
    margin-right: 15px;
    text-align: center;
  }
  .informationPersonMain > div, .informationPersonHobby > div{
    border: 1px solid #000;
    margin-top:5px;
    width: 250px;
    text-align: left;
  }
  .informationPersonHobby{
    margin-bottom: 15px;
  }
  .informationPersonMain > span, .informationPersonHobby >span{
    font-size: 24px;
    font-weight: 700;
  }

  .informationPersonMain > div, .informationPersonHobby >div{
    color:rgb(62, 62, 62);
    font-style: italic;
    font-weight: 500;
  }

  .informationPersonMain > div > span, .informationPersonHobby > div > span {
    font-weight: 700;
    font-size: 16px;
    color:#2c3e50;
    font-style: normal;
    
  }
  .informationPersonMain > div> span:hover, .informationPersonHobby >div> span:hover{
    color: #000;
  }
  .informationPersonMain > div:hover, .informationPersonHobby >div:hover {
    color:wheat
  }
  img{
    transition: 3s;
  }
  img:hover{
    transform: scale(1.35);
    position: relative;
    z-index: 2;
    border-radius: 0;
  }
</style>
