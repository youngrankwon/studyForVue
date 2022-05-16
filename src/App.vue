<template>
  <div class="black-bg" v-if="modal_status">
    <div class="white-bg">
      <h4>상세페이지임</h4>
      <p>상세페이지 내용임</p>
      <button @click="modal_status = false">닫기</button>
    </div>
  </div>
  <div>
    <p>MY SHOP</p>
    <div class="menu">
      <a v-for="(menu, i) in menuList" :key="i">{{i}}.{{menu}}</a>
    </div>
  </div>
  <div v-for="(product, i) in productList" :key="i">
    <img :src="product.image" style="room-img">
    <h4 @click="modal_status = true">{{product.title}}</h4>
    <p>{{product.price}} 만원</p>
    <!-- <button @click="addCart(i)">장바구니에 넣기</button> <span>장바구니수량 : {{cartCnts[i]}}</span> -->
  </div>
</template>

<script>
import productList from './assets/productList.js';


export default {
  name: 'App',
  data() {
    return {
      "productList" : productList,
      "price1" : 60,
      "price2" : 70,
      "products" : ['상품1', '상품2 ', '상품3'],
      "prices" : [60, 50, 70],
      "menuList" : ['Home', 'Product', 'About', 'Info'],
      "cartCnts" : [0, 0, 0],
      "modal_status" : false,
    }
  },
  methods:{
    addCart(index) {
      this.cartCnts[index] += 1;
    }
  },
  components: {

  }
}
</script>

<style>
body {
  margin:0;
}
.black-bg {
  width:100%; height: 100%;
  background: rgba(0,0,0,0.5);
  position: fixed; padding:20px;
}
.white-bg {
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 20px;
}
.menu{
  background : darkslateblue;
  padding:15px;
  border-radius: 5px;
}
.menu a {
  color:white;
  padding:10px
}
.room-img {
  width: 100%;
  height: 100%;
  margin:10px;
}


</style>
