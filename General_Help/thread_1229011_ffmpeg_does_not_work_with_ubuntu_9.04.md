---
title: "ffmpeg does not work with ubuntu 9.04"
date: 2009-08-01
forum: General Help
---

### Post by Dr Freedom on 2009-08-01
I have installed ubuntu 9.04 but ffmpeg is not working. After instaling it with the synaptic package manager, i get this error:

FFmpeg version 0.5-svn17737+3:0.svn20090303-1ubuntu6, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --extra-version=svn17737+3:0.svn20090303-1ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --disable-stripping --disable-vhook --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 10 2009 23:20:33, gcc: 4.3.3

Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 25.00 (25/1)
Input #0, flv, from '/home/vinny/Desktop/video CGI/Adoro te - RnS.flv':
  Duration: 00:04:03.40, start: 0.000000, bitrate: 327 kb/s
    Stream #0.0: Video: flv, yuv420p, 320x240, 263 kb/s, 25 tbr, 1k tbn, 1k tbc
    Stream #0.1: Audio: mp3, 22050 Hz, mono, s16, 64 kb/s
Unknown encoder 'libmp3lame'


I don't know what to do, can someone help me?

---

### Post by unutbu on 2009-08-01
> Unknown encoder 'libmp3lame'

Try installing the **libmp3lame0** package, then try ffmpeg again.

---

### Post by Dr Freedom on 2009-08-01
i did it and is not working, getting the same message.

I remember once i found a website where they showed how to download tons of codecs, it took about 10 minutes to download an install all of them, but after that ffmpeg worked perfectly. Unfortunately i can't find this web site anymore

---

### Post by unutbu on 2009-08-01
If you find it, please let us know.
In the mean time, have you tried this: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) ?

---

### Post by Dr Freedom on 2009-08-01
I did install Medibuntu and ffmpeg as described on the Ubuntu Forum but i get the same message. 

Untill i used the 8.10 ffmpeg was working fine, then i had the brilliant idea to upgrade the system and ffmpeg now is not working. I hope to solve this problem somehow

When i changed from 8.10 to 9.04 I did a complete new install.

---

### Post by andrew.46 on 2009-08-02
Hi Dr Freedom,

> **Dr Freedom said:**
> Untill i used the 8.10 ffmpeg was working fine, then i had the brilliant idea to upgrade the system and ffmpeg now is not working. I hope to solve this problem somehow

Have you had a look at the Fakeoutdoorsman's page:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

which describes the simple step required to unlock some of FFmpeg's codecs.

Andrew

---

