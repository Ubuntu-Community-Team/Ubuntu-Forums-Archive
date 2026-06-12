---
title: "creating Flashvideos with sound"
date: 2006-05-17
forum: General Help
---

### Post by ossi on 2006-05-17
Hi!

I tried to create some Flashvideos (.flv) for playback on the web. Mencoder seems not to be able to do it with my config (does anybody know a source with a package that can produce .flv's and probably playback dts??), but I could create videos with transcode and ffmpeg. 

The problem now is, that there is no sound in the videos. I get the following when encoding the video:

```
ossi@kajutr:~/video/springclassics06$ ffmpeg -i /home/ossi/video/springclassics06/springfin -ab 100 -ar 44100 -b 500 -r 15 -s 320*240 springfinalnu.flv
ffmpeg version CVS, build 3276800, Copyright (c) 2000-2004 Fabrice Bellard
* configuration: *--build i486-linux-gnu --enable-gpl --enable-pp --enable-zlib --enable-vorbis --enable-libogg --enable-theora --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --prefix=/usr
* built on Sep 29 2005 03:25:16, gcc: 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu8)
Input #0, mov,mp4,m4a,3gp,3g2, from '/home/ossi/video/springclassics06/springfin':
* Duration: 00:05:56.5, start: 0.000000, bitrate: 9394 kb/s
* Stream #0.0: Video: mpeg4, yuv420p, 720x576, 24.00 fps
* Stream #0.1: Audio: adpcm_ima_qt, 48000 Hz, stereo
File 'springfinalnu.flv' already exists. Overwrite ? [y/N] y
Output #0, flv, to 'springfinalnu.flv':
* Stream #0.0: Video: flv, yuv420p, 320x240, 15.00 fps, q=2-31, 500 kb/s
Stream mapping:
* Stream #0.0 -> #0.0
[flv @ 0x8333448]removing common factors from framerate
Press [q] to stop encoding
frame= 5349 q=0.0 Lsize= * 21852kB time=356.6 bitrate= 502.0kbits/s
video:21768kB audio:0kB global headers:0kB muxing overhead 0.384004%
```

Now trying to force an audio codec:

```
ossi@kajutr:~/video/springclassics06$ ffmpeg -i /home/ossi/video/springclassics06/springfin -acodec mp3 -ab 100 -ar 44100 -b 500 -r 15 -s 320*240 springfinalnu.flv
ffmpeg version CVS, build 3276800, Copyright (c) 2000-2004 Fabrice Bellard
* configuration: *--build i486-linux-gnu --enable-gpl --enable-pp --enable-zlib --enable-vorbis --enable-libogg --enable-theora --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --prefix=/usr
* built on Sep 29 2005 03:25:16, gcc: 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu8)
Input #0, mov,mp4,m4a,3gp,3g2, from '/home/ossi/video/springclassics06/springfin':
* Duration: 00:05:56.5, start: 0.000000, bitrate: 9394 kb/s
* Stream #0.0: Video: mpeg4, yuv420p, 720x576, 24.00 fps
* Stream #0.1: Audio: adpcm_ima_qt, 48000 Hz, stereo
File 'springfinalnu.flv' already exists. Overwrite ? [y/N] y
Output #0, flv, to 'springfinalnu.flv':
* Stream #0.0: Video: flv, yuv420p, 320x240, 15.00 fps, q=2-31, 500 kb/s
* Stream #0.1: Audio: 0x0000, 44100 Hz, stereo, 100 kb/s
Stream mapping:
* Stream #0.0 -> #0.0
* Stream #0.1 -> #0.1
[flv @ 0x8333448]removing common factors from framerate
Unsupported codec for output stream #0.1
```

I guess I do have that problems, because lame is not enabled. So there is no sound in ffmpeg and transcode. Do I really have to compile it myself, or is there somewhere a package, that works? Is there probably a way, that all of this works with mencoder (just because it's my favourite app)??

---

### Post by shanepardue on 2007-06-19
I got the same problem..did you find a way to get audio working in an flv file?

---

