---
title: "How to add codecs to WinFF"
date: 2009-06-30
forum: General Help
---

### Post by chipppy on 2009-06-30
***[SOLVED withthanks] Had to install all but finally got the right codec and all works great now.***

Good Evening

I am trying to convert an *.avi to *.vob(DVD) using WinFF.

I add the avi and set the device preset to NTSC DVD (4.3) and hit the convert button.

I got and error that *_Unknown encoder 'mpeg2video_* (full error message below). 
I added the bold to the second last line to highlight the error message

I did some searching on the WinFF site with no luck and tryed the good old google search and still no luck.

Is there someway for me to add this codec into WinFF?

Any and all assistance is greatly appreciated.

Cheers
chipppy

```
FFmpeg version 0.5-svn17737+3:0.svn20090303-1ubuntu6, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --extra-version=svn17737+3:0.svn20090303-1ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --disable-stripping --disable-vhook --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-armv6t2 --disable-armvfp --disable-neon --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 10 2009 23:18:41, gcc: 4.3.3
Input #0, avi, from '/home/learn01/Videos/Terminator Salvation 2009 re-encode ts Fatel.Rets/Terminator Salvation.avi':
  Duration: 01:45:10.96, start: 0.000000, bitrate: 932 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 608x256 [PAR 1:1 DAR 19:8], 25 tbr, 25 tbn, 25 tbc
    Stream #0.1: Audio: mp3, 44100 Hz, stereo, s16, 112 kb/s
**Unknown encoder 'mpeg2video'**
Press Enter to Continue

```

---

### Post by fooman on 2009-06-30
add the medibuntu repositories from here:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

 then install the ffmpeg from there.  if that does not do it...try installing "libavcodec-unstripped-51" (or 52)

hope that helps.

---

### Post by paul.gevers on 2009-06-30
> **fooman said:**
> add the medibuntu repositories from here:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

 then install the ffmpeg from there.

No need for the medibuntu ffmpeg for Jaunty.

> **fooman said:**
>   if that does not do it...try installing "libavcodec-unstripped-51" (or 52)

hope that helps.

That is the way to go, you need libavcodec-unstripped-52.

---

