---
title: "VLC problem with MPEG-4 encoding?"
date: 2010-12-06
forum: General Help
---

### Post by cptrohn on 2010-12-06
Hi I was going to use VLC to view some video files that I have that were copied with K9copy... when I go to open the file with VLC I get this error message from VLC  ```
No suitable decoder module:
VLC does not support the audio or video format "   ". Unfortunately there is no way for you to fix this.
```

So VLC can't play Mpeg-4?  That seems kind of odd to me since all the other players seem to be able to, can't imagine VLC not being able to do this....

---

### Post by karthick87 on 2010-12-06
Install the following codec

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by cptrohn on 2010-12-06
> **karthick87 said:**
> Install the following codec

```
sudo apt-get install ubuntu-restricted-extras
```

Already did that.. and installed ffmpeg and winff to make sure I have just about every conceiveable audio and video codec I can..... still get the same error message with VLC.... it plays fine in dragon, mplayer the default movie player etc.... just wondering why it won't in VLC....

---

### Post by TeoBigusGeekus on 2010-12-06
To see info about the file
```
ffmpeg -i filename.ext
```
Post us the output, I'm curious as well.

---

### Post by cptrohn on 2010-12-06
> **TeoBigusGeekus said:**
> To see info about the file
```
ffmpeg -i filename.ext
```
Post us the output, I'm curious as well.

Ok here is the output I get with that.
```
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:41:55, gcc: 4.4.3
[avi @ 0x1738480]non-interleaved AVI

Seems stream 0 codec frame rate differs from container frame rate: 59.94 (60000/1001) -> 29.97 (30000/1001)
Input #0, avi, from '4OnlySinDeep.avi':
  Duration: 00:27:17.98, start: 0.000000, bitrate: 5297 kb/s
    Stream #0.0: Video: mpeg2video, yuv420p, 720x480 [PAR 8:9 DAR 4:3], 9800 kb/s, 29.97 tbr, 29.97 tbn, 59.94 tbc
    Stream #0.1: Audio: ac3, 48000 Hz, stereo, s16, 192 kb/s
At least one output file must be specified

```


Not just 1 single file either, it's every file I have backed up with K9copy that I put into Mpeg-4.....

---

### Post by cptrohn on 2010-12-06
Just thought I would check in and see if anybody else had run across this problem or not....  LOL Guess I am the only one eh?

---

### Post by marko.games on 2010-12-06
I had the same problem. Reinstalling the system helped :D

---

### Post by Mariane on 2010-12-07
What, all of the system? Maybe it would fix this but then you would have to sort out again all the other problems... And one of these fixes would be bound to fail, so you would reinstall again... Never ending story. 

Mariane

---

### Post by cptrohn on 2010-12-07
> **marko.games said:**
> I had the same problem. Reinstalling the system helped :D

actually that doesn't help, this is on a fresh install as I just installed a new HD.  Oh well... I don't really need to use VLC anyway...  Was just curious.

---

