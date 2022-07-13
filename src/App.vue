<template>
  <canvas id="canvas"/>
</template>

<script setup lang="ts">
import { onMounted } from 'vue';

onMounted(() => {
  const stage = new createjs.Stage('canvas');
  const circle = new createjs.Shape();
  circle.graphics.beginFill('red').drawCircle(0, 0, 40);
  circle.x = circle.y = 50;
  stage.addChild(circle);
  circle.addEventListener('click', handleClick);

  function handleClick(event: any) {
    console.log(event);
  }

  createjs.Ticker.addEventListener('tick', handleTick);

  const g = new createjs.Graphics();
  g.setStrokeStyle(1);
  g.s('red').f('blue').r(20, 20, 100, 50);
  stage.addChild(new createjs.Shape(g));

  function handleTick(event: any) {
    // circle.x += 1;
    stage.update();
  }

  stage.update();
});
</script>
