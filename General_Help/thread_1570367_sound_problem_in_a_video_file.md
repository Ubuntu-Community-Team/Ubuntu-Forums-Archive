---
title: "sound problem in a video file"
date: 2010-09-08
forum: General Help
---

### Post by shaon3343 on 2010-09-08
[SIZE=3]hi there, I got a video file in which it produce sound in only one speaker , Looks like this sound comes from only one side. I can fix this temporaryly with my Smplayer ( audio--> filter-->volume normalization/ Extra_stereo/ karaoke ).  my other videos are perfectly well. So , how can I fix this issue parmanantly? I tested this video in windows xp ,and  same problem there !!
Please help [/SIZE]

---

### Post by ron999 on 2010-09-08
Hi
Please show some information about that video file.
Either use **mediainfo**
or use
```
ffmpeg -i video
```

---

### Post by shaon3343 on 2010-09-08
> **ron999 said:**
> Hi
Please show some information about that video file.
Either use **mediainfo**
or use
```
ffmpeg -i video
```

[SIZE=3]**Here it is : **[/SIZE]

>  shaon@shaon-desktop:/media/Refreshment/movie/tom_hanks$ ffmpeg -i Forrest_Gump.mkv
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:35:30, gcc: 4.4.3
[matroska @ 0x890c2c0]Unknown entry 0x80

Seems stream 0 codec frame rate differs from container frame rate: 50.00 (50/1) -> 25.00 (25/1)
Input #0, matroska, from 'Forrest_Gump.mkv':
  Duration: 02:15:08.60, start: 0.000000, bitrate: N/A
    Stream #0.0(eng): Video: h264, yuv420p, 350x178, PAR 159:175 DAR 159:89, 25 tbr, 1k tbn, 50 tbc
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, s16
At least one output file must be specified
shaon@shaon-desktop:/media/Refreshment/movie/tom_hanks$   

---

### Post by ron999 on 2010-09-08
Hi
We can use ffmpeg to create a new file with a repaired audio track.
This is the command:-
```
ffmpeg -i Forrest_Gump.mkv -vcodec copy -acodec libmp3lame -ac 1 new_file.mkv
```

The option **-vcodec copy** leaves the video track untouched.
When we encode the audio track the option **-ac 1** gives a mono soundtrack - from both speakers.

---

