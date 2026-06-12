---
title: "converting flash videos"
date: 2010-12-28
forum: General Help
---

### Post by ingrown.potato on 2010-12-28
Hello,

I want to be able to rip videos off youtube and put them on my ipod. I added installed "Download helper" which enables me to rip the videos off youtube in a flv format. When I try and convert the files to .mp4a (using the WinFF GUI) my terminal pops up and says "unknown encoder 'libx264'"

Here is the full message:

FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2.2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
configuration: --extra-version=4:0.5+svn20090706-2ubuntu2.2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 23 2010 15:05:49, gcc: 4.4.1

Seems stream 0 codec frame rate differs from container frame rate: 59.83 (29917/500) -> 59.75 (239/4)
Input #0, flv, from '/home/mike/Desktop/c++/C_Console_Lesson_1_Creating_a_Console_Application_  2010.flv':
  Duration: 00:03:15.77, start: 0.000000, bitrate: 221 kb/s
    Stream #0.0: Video: h264, yuv420p, 480x360 [PAR 1:1 DAR 4:3], 221 kb/s, 59.75 tbr, 1k tbn, 59.83 tbc
    Stream #0.1: Audio: aac, 44100 Hz, stereo, s16
Unknown encoder 'libx264'
Press Enter to Continue

--------------------------

Cam somebody help me out? Would it matter if I just did it in terminal instead of using the GUI? (just for the sake of learning, how would you use WinFF in terminal?)


Thanks!

---

### Post by ingrown.potato on 2010-12-28
bump

---

### Post by ingrown.potato on 2010-12-29
some one help!

---

### Post by andrew.46 on 2010-12-29
Perhaps have a look at this guide:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg 
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

Andrew

---

