---
title: "HELP: Ubuntu 9.10 fresh install, ffplay and melt crash"
date: 2009-11-08
forum: General Help
---

### Post by unutsch on 2009-11-08
Guys, I need your help: i just did a fresh install of Ubuntu 9.10, with no changes (i dl the live cd yesterday, and installed it, didnt upgrade it yet). I also installed ffplay (sudo apt-get install ffplay) and melt, and testet both of them with a .dv file that works: no luck, they both crash immediately.
Could you pls help me and get them to work? The thing is, that neither kdenlive (not the one installed from Karmics Softare Center, 0.75, and also not the 0.76 isntalled from the net) works (the preview monitor doesnt show the video when i press play, but if i move the cursor back and forth, i see the video)...

MELT ERROR: 
+-----+ +-----+ +-----+ +-----+ +-----+ +-----+ +-----+ +-----+ +-----+
|1=-10| |2= -5| |3= -2| |4= -1| |5=  0| |6=  1| |7=  2| |8=  5| |9= 10|
+-----+ +-----+ +-----+ +-----+ +-----+ +-----+ +-----+ +-----+ +-----+
+---------------------------------------------------------------------+
|               H = back 1 minute,  L = forward 1 minute              |
|                 h = previous frame,  l = next frame                 |
|           g = start of clip, j = next clip, k = previous clip       |
|                0 = restart, q = quit, space = play                  |
+---------------------------------------------------------------------+
Segmentation fault         4

FFPLAY ERROR:
FFplay version SVN-r19352-4:0.5+svn20090706-2ubuntu2, Copyright (c) 2003-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Oct 13 2009 22:15:16, gcc: 4.4.1
Segmentation fault

---

### Post by unutsch on 2009-11-08
I now isntalled libsdl1.2debian-pulseaudio and libsdl1.2debian-all - no changes: ffplay and melt still crash... anyone, please help me...

---

### Post by FakeOutdoorsman on 2009-11-08
How did you:
```
sudo apt-get install ffplay
```
I don't see this package in the 9.10 repository:
```
$ sudo apt-get install ffplay
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ffplay
```

---

### Post by unutsch on 2009-11-09
ffplay is just the command to launch ffmpeg's player... you need to install ffmpeg to use ffplay

[https://wiki.ubuntu.com/ffmpeg](https://wiki.ubuntu.com/ffmpeg)

---

### Post by FakeOutdoorsman on 2009-11-09
> **unutsch said:**
> ... I also installed ffplay **(sudo apt-get install ffplay)** and melt, ...

^ The reason I asked.

---

### Post by MZ007 on 2009-11-17
Hello Unutsch
Maybe you are using Ubuntu 9.10, kernel 2.6.28-16-generic ? I have the same problem when using this kernel.
It disappears when I use Ubuntu 9.10, kernel 2.6.31-14-generic.
However I have another problem: melt and kdenlive freeze randomly. Any idea about that?

---

