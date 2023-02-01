<template>
  <div class="background" style="position: absolute"></div>
</template>

<script>
export default {
  mounted() {
    make_divs();
    window.addEventListener('onload', () => this.make_divs());
  },
};
window.onload = function () {
  make_divs();
  console.log('did it');
};

function make_divs() {
  let width = document.getElementsByClassName('background')[0].offsetHeight / 4;
  let parent = document.getElementsByClassName('background')[0];

  console.log(width);
  let divs = [];

  for (let x = 0; x < width; x++) {
    divs.push(document.createElement('div'));
  }

  for (let x = 0; x < divs.length; x++) {
    let pixels = Math.floor(Math.random() * 300);
    if (x % 2 == 0) {
      divs[x].classList.add('hover-color');
      divs[
        x
      ].style.cssText += `max-width:${pixels}px;height:4px;background-color: orange;`;
    } else {
      divs[x].style.cssText += `max-width:${pixels}pxheight:4px;`;
    }

    let rand = Math.floor(Math.random() * width);
    divs[rand].style['background-color'] = 'red';

    parent.appendChild(divs[x]);
    parent.style.cssText += 'background-color: orange';
    document.documentElement.style.setProperty('--width-percentage', '100%');
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
:root {
  --width-percentage: 100%;
  --width-end-percentage: 0%;
}

.background {
  background-color: orange;
  width: 100%;
  height: 100%;
  min-width: 1500px;
  min-height: 1500px;
  position: relative;
  z-index: 10;
}
.hover-color {
  animation-name: usdp;
  animation-duration: 2.5s;
  animation-iteration-count: infinite;
  animation-timing-function: ease-in-out;
}
.hover-color2 {
  animation-name: usdp2;
  animation-duration: 1.5s;
  animation-iteration-count: infinite;
  animation-timing-function: ease-in-out;
}
@keyframes usdp {
  from {
    width: var(--width-percentage);
  }
  50% {
    width: var(--width-end-percentage);
  }
  to {
    width: var(--width-percentage);
  }
}
@keyframes usdp2 {
  from {
    width: var(--width-percentage);
  }
  50% {
    width: var(--width-end-percentage);
  }
  to {
    width: var(--width-percentage);
  }
}
.background:hover {
}
h3 {
  margin: 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0px;
}
a {
  color: #42b983;
}
</style>
