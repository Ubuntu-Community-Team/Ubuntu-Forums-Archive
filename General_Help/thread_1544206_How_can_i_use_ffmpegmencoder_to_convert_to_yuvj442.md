---
title: "How can i use ffmpeg/mencoder to convert to yuvj442p ??"
date: 2010-08-02
forum: General Help
---

### Post by peturingi on 2010-08-02
Hi.

I have some video files (.avi and .swf) & I need to convert them to the following format:

    Stream #0.0(eng): Video: mjpeg, yuvj422p, 320x240, 30 tbr, 30 tbn, 30 tbc
    Stream #0.1(eng): Audio: pcm_u8, 8000 Hz, mono, s16, 64 kb/s

Can you tell me how to do this with mencoder or ffmpeg?

---

### Post by FakeOutdoorsman on 2010-08-02
Try this:
```
ffmpeg -i input.avi -vcodec mjpeg -pix_fmt yuvj422p -qscale 3 -s 320x240 -r 30 \
-acodec pcm_u8 -ar 8000 -ac 1 -ab 64k output.avi
```
This results in:
```
$ ffmpeg -i output.avi
Stream #0.0: Video: mjpeg, yuvj422p, 320x240, 30 tbr, 30 tbn, 30 tbc
Stream #0.1: Audio: pcm_u8, 8000 Hz, 1 channels, u8, 64 kb/s
```
*pcm_u8* and *s16* seem contradictory to me.

---

### Post by peturingi on 2010-08-04
> **FakeOutdoorsman said:**
> Try this:
```
ffmpeg -i input.avi -vcodec mjpeg -pix_fmt yuvj422p -qscale 3 -s 320x240 -r 30 \
-acodec pcm_u8 -ar 8000 -ac 1 -ab 64k output.avi
```This results in:
```
$ ffmpeg -i output.avi
Stream #0.0: Video: mjpeg, yuvj422p, 320x240, 30 tbr, 30 tbn, 30 tbc
Stream #0.1: Audio: pcm_u8, 8000 Hz, 1 channels, u8, 64 kb/s
```*pcm_u8* and *s16* seem contradictory to me.

It's not working for me.
Here is the complete output:

```

petur@petur-laptop:~/Desktop/videoconv$ **ffmpeg -i xPU8OAjjS4k.flv -vcodec mjpeg -pix_fmt yuvj422p -qscale 3 -s 320x240 -r 30 -acodec pcm_u8 -ar 8000 -ac 1 -ab 64k output.avi**
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

Seems stream 0 codec frame rate differs from container frame rate: 60.00 (60/1) -> 29.97 (30000/1001)
Input #0, flv, from 'xPU8OAjjS4k.flv':
  Duration: 00:03:54.76, start: 0.000000, bitrate: 820 kb/s
    Stream #0.0: Video: h264, yuv420p, 640x480 [PAR 1:1 DAR 4:3], 820 kb/s, 29.97 tbr, 1k tbn, 60 tbc
    Stream #0.1: Audio: aac, 44100 Hz, stereo, s16
Output #0, avi, to 'output.avi':
    Stream #0.0: Video: mjpeg, yuvj422p, 320x240 [PAR 1:1 DAR 4:3], q=2-31, 200 kb/s, 90k tbn, 30 tbc
    Stream #0.1: Audio: pcm_u8, 8000 Hz, mono, u8, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
frame= 7044 fps= 41 q=3.0 Lsize=  135153kB time=234.80 bitrate=4715.4kbits/s    
video:132897kB audio:1838kB global headers:0kB muxing overhead 0.310401%
petur@petur-laptop:~/Desktop/videoconv$ ffmpeg -i output.avi 
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
Input #0, avi, from 'output.avi':
  Duration: 00:03:55.28, start: 0.000000, bitrate: 4705 kb/s
[B]    Stream #0.0: Video: mjpeg, yuvj422p, 320x240, PAR 1:1 DAR 4:3, 30 tbr, 30 tbn, 30 tbc
    Stream #0.1: Audio: pcm_u8, 8000 Hz, mono, s16, 64 kb/s
[/B]At least one output file must be specified
petur@petur-laptop:~/Desktop/videoconv$ 


```

I need the output to be exacly as stated in the first post, else my playback device won't play it (a panasonic camera)

---

### Post by FakeOutdoorsman on 2010-08-04
> **peturingi said:**
> It's not working for me.
Do you mean FFmpeg isn't working, or it didn't play on your camera correctly?

> **peturingi said:**
> I need the output to be exacly as stated in the first post, else my playback device won't play it (a panasonic camera)
This may prove to be tricky.  Can you provide more information on a video that does work? Use [mediainfo](http://mediainfo.sourceforge.net/) to inspect the video and show the output.

---

### Post by peturingi on 2010-08-05
> **FakeOutdoorsman said:**
> [QUOTE=peturingi;9676796]It's not working for me.[quote]
Do you mean FFmpeg isn't working, or it didn't play on your camera correctly?


This may prove to be tricky.  Can you provide more information on a video that does work? Use [mediainfo]("http://mediainfo.sourceforge.net/") to inspect the video and show the output.

FFmpeg works, but my device is unable to play the file produced.

mediainfo is not in the official repos.

---

