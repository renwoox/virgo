<template>
  <div>
    <modal
      v-bind="{
        visible: !!video,
        side: 'center',
        buttonClose: true,
        fullscreen: true,
        width: '900px',
        backgroundColor: 'rgba(0,0,0,.8)'
      }"
      @visible="video = $event"
      v-if="!!video"
    >
      <div class="modal__content" v-if="!!video">
        <iframe
          width="100%"
          height="510"
          src="https://www.youtube.com/embed/cD57_QKToa8?autoplay=1&amp;controls=1&amp;rel=0&amp;modestbranding=1&amp;fs=1"
          frameborder="0"
          allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture"
          allowfullscreen="allowfullscreen"
        ></iframe>
      </div>
    </modal>
    <div id="site-hero">
      <div id="video-container">
        <video id="video-bg" autoplay loop muted playsinline>
          <source :src="$frontmatter.webm" type="video/webm" />
          <source :src="$frontmatter.mpeg" type="video/mp4" />
        </video>
      </div>
      <div class="site-hero__text">
        <h1>Open collaboration tools for everyone.</h1>
        <p>
          Virgo recommends easy-to-use tools for decentralized collaboration.
          Better coordination will help us solve difficult challenges, such
          climate change, environmental destruction, and providing for basic
          human needs.
        </p>
        <div class="vg-btns">
          <a class="vg-btn vg-btn__primary" @click="video = true"
            >Watch video
            <icon-play />
          </a>
          <a class="vg-btn" href="/act">
            Take action
            <icon-check />
          </a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import IconPlay from "../icons/frame-c-caret-right";
import IconCheck from "../icons/f-check";
import { Modal, CookieBanner } from "@cosmos-ui/vue";
export default {
  components: {
    IconCheck,
    IconPlay,
    Modal,
    CookieBanner
  },
  data: () => ({
    video: null
  })
};
</script>

<style scoped lang="stylus">
.modal__content
  background #000
  width 100vw
  max-width 896px
  line-height 0
  display flex
  align-items center

#site-hero
  width 100vw
  height 100vh
  display flex
  align-items center
  justify-content center
  padding-top 3em

.site-hero__text
  color #fff
  z-index 1
  text-shadow #000 0 2px 3px
  padding 0 1em

#video-container
  position absolute
  top 0
  left 0
  width 100vw
  height 100vh
  background #000
  overflow hidden
  &:after
    content ""
    width 100vw
    height 100vh
    background url('../images/matrix-90.png')
    display block
    position absolute
    top 0
    left 0
    z-index 1

.vg-btns
  display flex
  flex-flow column nowrap
  margin-top 2rem

.vg-btn
  font-family var(--sans)
  display inline-block
  height 3em
  line-height 3em
  padding 0 1em
  background hsla(0, 100%, 0%, 0.75)
  color #fff
  border none
  text-shadow none
  cursor pointer
  display flex
  align-items center
  justify-content center
  &:hover
    opacity 0.85
  svg
    margin-left 0.5rem

.vg-btn__primary
  background hsl(170,75%,40%)

.vg-btn + .vg-btn
  margin-top 0.5rem

@media (min-aspect-ratio: 16/9)
  #video-bg
    width 100%
    height auto

@media (max-aspect-ratio: 16/9)
  #video-bg
    width auto
    height 100%

@media screen and (min-width: 375px)
  .vg-btns
    display flex
    flex-flow row wrap

  .vg-btn + .vg-btn
    margin-left 1rem
    margin-top 0

@media screen and (min-width: 768px)
  .site-hero__text
    font-size 1.25rem
    margin-left 12.5vw
    margin-right 12.5vw

@media screen and (min-width: 1024px)
  .site-hero__text
    text-align center
    padding-left 12.5vw
    padding-right 12.5vw
    .vg-btns
      justify-content center
    p
      margin 2em 0
</style>
