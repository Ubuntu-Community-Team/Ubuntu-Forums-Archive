---
title: "can't streaming webcam with ffserver and ffmpeg"
date: 2006-04-16
forum: General Help
---

### Post by tassoman on 2006-04-16
Hi all,
I'm trying to stream my webcam (/dev/video1), it's a quickcam working by video4linux.

When i try to encode /dev/video1 to ffserver, i get that error from ffmpeg:
```
tassoman@lumaco:~$ ffmpeg -vd /dev/video1 -an -b 128 -r 15 -s 352x240 -vcodec mpeg4 http://localhost:8090/feed1.ffm
ffmpeg version CVS, build 3276800, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --build i486-linux-gnu --enable-gpl --enable-pp --enable-zlib --enable-vorbis --enable-libogg --enable-theora --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --prefix=/usr
  built on Sep 29 2005 03:25:16, gcc: 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu8)
Input #0, video4linux, from '':
  Duration: N/A, bitrate: N/A
  Stream #0.0: Video: rawvideo, yuv422, 352x240, 15.00 fps
Input #1, audio_device, from '':
  Duration: N/A, bitrate: N/A
  Stream #1.0: Audio: pcm_s16le, 44100 Hz, mono, 705 kb/s
picture size invalid (0x329)
Segmentation fault

```

this is version from apt, and in configuration seems not compiled with v4l.
Maybe this is the error? Should i recompile with v4l enabled ?

---

