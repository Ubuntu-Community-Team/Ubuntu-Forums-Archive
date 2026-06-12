---
title: "Converting file using ffmpeg trouble"
date: 2010-08-16
forum: General Help
---

### Post by kmccmk9 on 2010-08-16
hello i have tried many different ways to get this conversion to work but I can't seem to get it to work. The source is .mov. Here is the command I used and the errors that I recieved

[PHP]kyle@kyle-linux:~$ cd Desktop
kyle@kyle-linux:~/Desktop$ clear

kyle@kyle-linux:~/Desktop$ ffmpeg -i maclinux.mov maclinux.mpg
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
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x82da2c0]multiple edit list entries, a/v desync might occur, patch welcome
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'maclinux.mov':
  Duration: 00:03:42.84, start: 0.000000, bitrate: 71585 kb/s
    Stream #0.0(eng): Video: Apple Intermediate Codec, 1440x900, 600 tbr, 600 tbn, 600 tbc
    Stream #0.1(eng): Audio: aac, 44100 Hz, mono, s16
swScaler: Unknown format is not supported as input pixel format
Cannot get resampling context
kyle@kyle-linux:~/Desktop$ 
[/PHP]

It gets all information correct but something goes wrong after that.

---

### Post by kmccmk9 on 2010-08-16
Ok so I finally got that one to convert to mp4 but now I'm trying to get this file to convert but why am I getting this error?

kyle@kyle-linux:~$ ffmpeg -i linuxinstall.ogv linuxinstall.mp4
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
Input #0, ogg, from 'linuxinstall.ogv':
  Duration: 00:04:02.20, start: 0.000000, bitrate: 1564 kb/s
    Stream #0.0: Invalid Codec type -1
    Stream #0.1: Video: theora, yuv420p, 1440x896, PAR 1:1 DAR 45:28, 15 tbr, 15 tbn, 15 tbc
    Stream #0.2: Audio: vorbis, 22050 Hz, mono, s16, 89 kb/s
Output #0, mp4, to 'linuxinstall.mp4':
    Stream #0.0: Video: mpeg4, yuv420p, 1440x896 [PAR 1:1 DAR 45:28], q=2-31, 200 kb/s, 90k tbn, 15 tbc
    Stream #0.1: Audio: 0x0000, 22050 Hz, mono, s16, 64 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
  Stream #0.2 -> #0.1
[mpeg4 @ 0x9ca33a0]removing common factors from framerate
Unsupported codec for output stream #0.1
kyle@kyle-linux:~$

---

### Post by kmccmk9 on 2010-08-16
All of the videos come out with weird discoloration. Audio is perfect though

---

### Post by FakeOutdoorsman on 2010-08-16
What is your final destination or device for your videos (web, playback on computer, YouTube, phone, DVD, iPod, etc)?

recordMyDesktop creates videos that are not compatible with older versions of FFmpeg.  This is probably either due to recordMyDesktop making bad or non-standard output files, or FFmpeg lacking the ability to decode them for some reason.  You can:

1. Use a newer FFmpeg. More recent FFmpeg can handle these videos:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

or

2. Use a different encoder, such as MEncoder, that can handle these videos. Some examples are shown here:

[HOWTO: Convert ogv to avi and upload to youtube](http://ubuntuforums.org/showthread.php?t=1501566)

---

### Post by kmccmk9 on 2010-08-18
> **FakeOutdoorsman said:**
> What is your final destination or device for your videos (web, playback on computer, YouTube, phone, DVD, iPod, etc)?

recordMyDesktop creates videos that are not compatible with older versions of FFmpeg.  This is probably either due to recordMyDesktop making bad or non-standard output files, or FFmpeg lacking the ability to decode them for some reason.  You can:

1. Use a newer FFmpeg. More recent FFmpeg can handle these videos:

[HOWTO: Install and use the latest FFmpeg and x264]("http://ubuntuforums.org/showthread.php?t=786095")

or

2. Use a different encoder, such as MEncoder, that can handle these videos. Some examples are shown here:

[HOWTO: Convert ogv to avi and upload to youtube]("http://ubuntuforums.org/showthread.php?t=1501566")

Thank You very much. That howto guide fixed my problem.

---

