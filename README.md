# canvas2video

![](https://img.shields.io/npm/v/canvas2video.svg?style=flat-square)

Convert dynamic canvas to video, support merge audio (use [ffmpeg.wasm](https://github.com/ffmpegwasm/ffmpeg.wasm))

## Install

```js
npm i canvas2video
```

## Usage

```js
import { Canvas2Video } from "canvas2video";
```

```html
<script src="https://unpkg.com/canvas2video/dist/canvas2video.js"></script>
<!--if convert video type or merge audio, must be include ffmpeg.js in html file -->
<script src="https://unpkg.com/@ffmpeg/ffmpeg/dist/ffmpeg.min.js"></script>
<script>
  const canvas = document.querySelector("canvas");
  const instance = new Canvas2Video({
    canvas: canvas,
    workerOptions: {
      // logger: str => console.error(str),
    },
    // audio: 'http://s5.qhres.com/static/465f1f953f1e6ff2.mp3'
  });
  instance.startRecord();

  setTimeout(() => {
    instance.stopRecord();
  }, 3000);

  instance
    .getStreamURL()
    .then((url) => {
      console.log("video url", url);
    })
    .catch((err) => console.error(err));
</script>
```

## Demo

- [canvas to video](./demo/index.html)
- [canvas to video, convert to mp4](./demo/mp4.html)
- [canvas to video, convert to mp4, merge audio](./demo/audio.html)
