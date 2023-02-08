<template>
  <div>
    <img alt="gallery" v-imageSrc="{ srcs: arr, time: 2000 }" />
  </div>
</template>

<script>
export default {
  directives: {
    imageSrc: {
      mounted(el, binding) {
        if (binding.modifiers.random) {
          setInterval(() => {
            let random = Math.floor(
              Math.random() * (binding.value.srcs.length + 1)
            )
            el.src = binding.value.srcs[random]
          }, binding.value.time)
        } else {
          let counter = 0
          setInterval(() => {
            el.src = binding.value.srcs[counter]
            counter++
            if (counter >= binding.value.srcs.length) {
              counter = 0
            }
          }, binding.value.time)
        }
      },
    },
  },

  data() {
    return {
      arr: [
        'https://wp-s.ru/wallpapers/9/1/547422858285832/grand-kanon-v-arizone-ssha.jpg',
        'https://vsegda-pomnim.com/uploads/posts/2022-04/1649332183_63-vsegda-pomnim-com-p-karibskoe-more-plyazh-foto-75.jpg',
        'https://avrorra.com/wp-content/uploads/2018/12/post_5c1287083cdaf.jpeg',
        'https://avatars.dzeninfra.ru/get-zen_doc/1588093/pub_5d8074f698fe7900ac84aca8_5d8084d9a660d700ae52af35/scale_1200',
        'https://vsegda-pomnim.com/uploads/posts/2022-03/1648753820_2-vsegda-pomnim-com-p-ozero-baikal-zima-foto-2.jpg',
      ],
    }
  },
}
</script>

<style>
img {
  height: 300px;
}
</style>
