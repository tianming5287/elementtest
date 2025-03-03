<script setup>
import { ref } from 'vue';

const fcount = ref(0);
const scount = ref(0);

const debounce =(fn,delay)=>{
    let timeId = null;
    return function(...args){
        if(timeId){
            clearTimeout(timeId);
        }
        timeId = setTimeout(()=>{
            fn(...args)
        },delay)
    }
}

const clickhandler = debounce(()=>{
    scount.value++;},500)
</script>
<template>
    <div class="box">
        <div class="first">
            <el-button type="primary" @click="fcount++">normal按钮</el-button>
            <span class="second">{{ fcount }}</span>
        </div>
        <div class="first">
            <el-button type="primary" @click="clickhandler">debounce按钮</el-button>
            <span class="second">{{ scount }}</span>
        </div>
    </div>
</template>
<style>
.box{
    display: flex;
    gap:30px;
}
.first{
    display: flex;
    flex-direction: column;
    align-items: center;
    /* margin-top: 30px; */
}
.second{
    margin-top: 20px;
}
</style>