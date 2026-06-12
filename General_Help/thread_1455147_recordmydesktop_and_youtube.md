---
title: "recordmydesktop and youtube"
date: 2010-04-15
forum: General Help
---

### Post by linden940 on 2010-04-15
ok i am at a lost here....tryed a few things and still cant get it to work right....maybe one of ya'll ran into this and found a fix.

here is a small video clip
[http://www.youtube.com/watch?v=K_NenyJY9tM](http://www.youtube.com/watch?v=K_NenyJY9tM)

the ogv file DOS NOT look like that...but once i upload it TO youtube it dos that...it wont play right.

any ideas?

---

### Post by WinterRain on 2010-04-15
Did you convert your file to flash before uploading to youtube? You can use Winff to do this.

---

### Post by linden940 on 2010-04-15
no i had not...never had a problem uploading the ogv files to youtube

---

### Post by linden940 on 2010-04-15
bump

---

### Post by linden940 on 2010-04-15
[https://bugs.launchpad.net/ubuntu/+source/recordmydesktop/+bug/544463](https://bugs.launchpad.net/ubuntu/+source/recordmydesktop/+bug/544463)

there IS a bug....anyone know a workaround?

---

### Post by linden940 on 2010-04-15
bump

---

### Post by Perfect Storm on 2010-04-15
Please do not bump a thread within 24 hours, thanks.


Does it have to be ogv? Just upload it as .avi

---

### Post by WinterRain on 2010-04-15
Until you can figure out how to fix this problem, why not just use winff to convert to flash vid?

Btw, it's frowned upon to bump the thread every few minutes. You could also start another thread at linuxforums.org or something.

---

### Post by linden940 on 2010-04-15
i'll keep that in mind on the bumpin part


winff....same problem...only thing is..when I try to play it back on MY own computer with out uploading it to youtube...I cant watch the video..its all messed up

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
[ogg @ 0x1c27480]Could not find codec parameters (Invalid Codec type -1)
Input #0, ogg, from '/home/ubuntu/Desktop/11.ogv':
  Duration: 00:00:02.60, start: 0.000000, bitrate: 1705 kb/s
    Stream #0.0: Invalid Codec type -1
    Stream #0.1: Video: theora, yuv420p, 1360x768, PAR 1:1 DAR 85:48, 15 tbr, 15 tbn, 15 tbc
    Stream #0.2: Audio: vorbis, 22054 Hz, mono, s16, 89 kb/s
Output #0, flv, to '/home/ubuntu/Desktop/11.flv':
    Stream #0.0: Video: flv (hq), yuv420p, 320x240 [PAR 1:1 DAR 4:3], q=2-31, 300 kb/s, 90k tbn, 29.97 tbc
    Stream #0.1: Audio: libmp3lame, 22050 Hz, mono, s16, 56 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
  Stream #0.2 -> #0.1
Press [q] to stop encoding
frame=   76 fps= 71 q=2.0 Lsize=     241kB time=2.46 bitrate= 803.5kbits/s    
video:221kB audio:17kB global headers:0kB muxing overhead 1.237775%
Press Enter to Continue

```

---

### Post by Perfect Storm on 2010-04-16
> [ogg @ 0x1c27480]Could not find codec parameters (Invalid Codec type -1)

Do you have the different codecs installed?

---

### Post by linden940 on 2010-04-16
hmmm guess not...where would i find the other codec that i dont have?

---

### Post by linden940 on 2010-04-17
ok...i keeped playing with it and I found a fix....using a prgram called Transmageddon found in the Ubuntu software center....and it was able to change the format from ogv to flv...and was able to play it back on the computer clear with out looking like i was on crack...uploaded it to youtube and it worked there as well...so this has been fixed.

---

