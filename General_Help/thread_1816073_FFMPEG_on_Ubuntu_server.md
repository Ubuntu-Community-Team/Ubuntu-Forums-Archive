---
title: "FFMPEG on Ubuntu server"
date: 2011-08-01
forum: General Help
---

### Post by U2XS on 2011-08-01
I use FFMPEG on my laptop all of the time & it's great.  I wanted to set it up on a server so that I can bulk process files using FFMPEG.  But I can't get it to work!  I think that the problem is in the setup.  On my laptop, I have a GUI & use point & click operations.  I think that I am missing something required to convert this video.

 - I've added Medibuntu repositories.
 - I have Ubuntu 10.04 on it
 - I've added FFMPEG from the Ubuntu repositories (built March 31, 2011).

Enclosed is the error I see as an output




```
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1.1, Copyright (c) 2000-2009 Fabrice Be                                           llard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1.1 --prefix=/usr --enable-avfil                                           ter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enabl                                           e-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enab                                           le-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-c                                           pudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enab                                           le-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar 31 2011 18:53:20, gcc: 4.4.3

Seems stream 0 codec frame rate differs from container frame rate: 2000.00 (2000                                           /1) -> 24.00 (24/1)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'testFile.mp4':
  Duration: 00:07:45.62, start: 0.000000, bitrate: 2563 kb/s
    Stream #0.0(und): Video: h264, yuv420p, 1280x720, 24 tbr, 1k tbn, 2k tbc
    Stream #0.1(und): Audio: aac, 44100 Hz, stereo, s16
Output #0, mp3, to '/var/www/test/testFile.mp3':
    Stream #0.0(und): Audio: 0x0000, 44100 Hz, stereo, s16, 192 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
Unsupported codec for output stream #0.0
administrator@ubuntuServer:/var/www/test$

```

---

### Post by AlphaLexman on 2011-08-01
There is an excellent tutorial at [this thread]("http://ubuntuforums.org/showthread.php?t=786095&highlight=ffmpeg").

---

### Post by U2XS on 2011-08-01
It's a great looking tutorial.  I ran through the motions (uninstalling & reinstalling their way) and came up with the same error though...

I imagine that someone had come across this issue before.

---

### Post by FakeOutdoorsman on 2011-08-01
Please show your FFmpeg command too.

---

### Post by U2XS on 2011-08-01
It looks like this one is my problem.  One of the codecs is not installed or configured maybe?
```
Encoder (codec id 86017) not found for output stream #0.0
```

The full output (with command) is here.


```
administrator@ubuntuServer:~/test$ sudo ffmpeg -i testFile.mp4 -vn -ar 44100 -ac 2 -ab 192000 -f mp3 /                                                                           var/www/test/testFile.mp3
ffmpeg version N-31717-g29d854d, Copyright (c) 2000-2011 the FFmpeg developers
  built on Aug  1 2011 12:12:22 with gcc 4.4.3
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-libfaac --                                                                           enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-lib                                                                           x264 --enable-libxvid --enable-x11grab
  libavutil    51. 11. 1 / 51. 11. 1
  libavcodec   53.  9. 0 / 53.  9. 0
  libavformat  53.  6. 0 / 53.  6. 0
  libavdevice  53.  2. 0 / 53.  2. 0
  libavfilter   2. 27. 5 /  2. 27. 5
  libswscale    2.  0. 0 /  2.  0. 0
  libpostproc  51.  2. 0 / 51.  2. 0

Seems stream 0 codec frame rate differs from container frame rate: 59.83 (29917/500) -> 29.92 (359/12)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'testFile.mp4':
  Metadata:
    major_brand     : mp42
    minor_version   : 0
    compatible_brands: isommp42
    creation_time   : 2010-10-24 06:46:22
  Duration: 00:03:48.28, start: 0.000000, bitrate: 915 kb/s
    Stream #0.0(und): Video: h264 (High), yuv420p, 1280x720 [SAR 1:1 DAR 16:9], 781 kb/s, 29.97 fps, 2                                                                           9.92 tbr, 1k tbn, 59.83 tbc
    Metadata:
      creation_time   : 1970-01-01 00:00:00
    Stream #0.1(und): Audio: aac, 44100 Hz, stereo, s16, 127 kb/s
    Metadata:
      creation_time   : 2010-10-24 06:46:24
File '/var/www/test/testFile.mp3' already exists. Overwrite ? [y/N] y
Output #0, mp3, to '/var/www/test/testFile.mp3':
    Stream #0.0(und): Audio: [0][0][0][0] / 0x0000, 44100 Hz, 2 channels, s16, 64 kb/s
    Metadata:
      creation_time   : 2010-10-24 06:46:24
Stream mapping:
  Stream #0.1 -> #0.0
Encoder (codec id 86017) not found for output stream #0.0
administrator@ubuntuServer:~/test$
```

---

### Post by FakeOutdoorsman on 2011-08-01
Your command looks like it was truncated. Can you post the complete command?

---

### Post by nipennem on 2011-08-01
> **FakeOutdoorsman said:**
> Your command looks like it was truncated. Can you post the complete command?

Just scroll further to the right, the rest is there but with lots of whitespace.

Would [this thread on Stack Overflow]("http://stackoverflow.com/questions/5021120/ffmpeg-mp3-conversion-failed") be of any help?

---

### Post by FakeOutdoorsman on 2011-08-01
> **U2XS said:**
> 
```

Output #0, mp3, to '/var/www/test/testFile.mp3':
    Stream #0.0(und): Audio: [0][0][0][0] / 0x0000, 44100 Hz, 2 channels, s16, 64 kb/s
    Metadata:
      creation_time   : 2010-10-24 06:46:24
Stream mapping:
  Stream #0.1 -> #0.0
Encoder (codec id 86017) not found for output stream #0.0

```
The problem is that your FFmpeg has not been configured with *--enable-libmp3lame*, so you can not encode to mp3. Uninstall your compiled FFmpeg and either re-compile it with libmp3lame support, or simply install it from the repository:
```
sudo apt-get remove ffmpeg
sudo apt-get install ffmpeg libavcodec-extra-52
```

> **nipennem said:**
> Just scroll further to the right, the rest is there but with lots of whitespace.
Thanks. Didn't see that.

---

### Post by U2XS on 2011-08-01
> **FakeOutdoorsman said:**
> The problem is that your FFmpeg has not been configured with *--enable-libmp3lame*, so you can not encode to mp3. Uninstall your compiled FFmpeg and either re-compile it with libmp3lame support, or simply install it from the repository:
```
sudo apt-get remove ffmpeg
sudo apt-get install ffmpeg libavcodec-extra-52
```
Thanks. Didn't see that.
Thanks!  It looks like reinstalling from the ubuntu repositories with "libavcodec-extra-52" was all I needed.  Now, it works like a charm.

---

