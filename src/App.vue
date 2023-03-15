/*
 * @Author: web.王晓冬
 * @Date: 2021-08-20 19:10:57
 * @LastEditors: web.王晓冬
 * @LastEditTime: 2021-10-10 22:33:02
 * @Description: file content
*/
<template>
  <!-- <div style="height:150px; margin-top:100px">
    <d-slider v-model="options.volume"></d-slider>
  </div>-->
  <div style="text-align: center">
    <button
      @click="options.src = 'http://krtxplay1.setrtmp.com/live/SSAC-235125-DFBCE.m3u8'"
    >{{ options.src }}</button>
    <videoPlay ref="video" style="display: inline-block; width: 100%" v-bind="options" v-if="state.show"/>
    <button
      @click="hide"
    >hide video</button>
    <button
      @click="show"
    >show video</button>
  </div>
</template>

<script setup lang="ts">
import { reactive, ref, nextTick } from "vue";
import { videoPlay } from "../lib/index.js";

const state = reactive({
  show: true,
})

const options = reactive({
  width: "800px",
  height: "450px",
  color: "#409eff",
  muted: false, //静音
  webFullScreen: false,
  autoPlay: true, //自动播放
  currentTime: 0,
  loop: false, //循环播放
  mirror: false, //镜像画面
  ligthOff: false, //关灯模式
  volume: 0.3, //默认音量大小
  control: true, //是否显示控制器
  title: "", //视频名称
  type: "m3u8",
  src: "http://113.121.231.37:18000/hls/34020000002000000001_37140000011327534560_0400004560/playlist.m3u8", //视频源
  // src: "https://cdn.jsdelivr.net/gh/xdlumia/files/video-play/IronMan.mp4", //视频源
  // src: "https://logos-channel.scaleengine.net/logos-channel/live/biblescreen-ad-free/playlist.m3u8", //视频源
  poster: "https://cdn.jsdelivr.net/gh/xdlumia/files/video-play/ironMan.jpg", //封面
  controlBtns: [
    "audioTrack",
    "quality",
    "speedRate",
    "volume",
    "setting",
    "pip",
    "pageFullScreen",
    "fullScreen",
  ],
});
const video = ref();

function hide(){
  state.show = false
  options.src = ""
  video.value.dispose()
  // console.log(video.value)
}

function show(){
  state.show = true
  options.src = "http://113.121.231.37:18000/hls/34020000002000000001_37140000011327534560_0400004560/playlist.m3u8"
}
</script>

<style scoped>
</style>
