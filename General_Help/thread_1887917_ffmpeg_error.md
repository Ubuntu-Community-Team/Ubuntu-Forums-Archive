---
title: "ffmpeg error"
date: 2011-11-28
forum: General Help
---

### Post by chrisc200 on 2011-11-28
On 11.10 I compiled ffmpeg using the info from here with all options enabled:

[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

on all avi's I encode, I get the following error in bold.
Why is this? I tried some other avi's still same error. What do I need to do to fix it
thanks


```
chris@chris-dell:~/Desktop$ ffmpeg -i eastenders.avi -acodec libfaac -aq 100 -vcodec libx264 -preset slow -crf 22 output.mp4
ffmpeg version git-2011-11-26-8f37c8f, Copyright (c) 2000-2011 the FFmpeg developers
  built on Nov 28 2011 11:38:37 with gcc 4.6.1
  configuration: --enable-gpl --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libx264 --enable-nonfree --enable-postproc --enable-version3 --enable-x11grab --enable-libvpx
  libavutil    51. 29. 1 / 51. 29. 1
  libavcodec   53. 37. 1 / 53. 37. 1
  libavformat  53. 21. 0 / 53. 21. 0
  libavdevice  53.  4. 0 / 53.  4. 0
  libavfilter   2. 50. 0 /  2. 50. 0
  libswscale    2.  1. 0 /  2.  1. 0
  libpostproc  51.  2. 0 / 51.  2. 0
[mpeg4 @ 0x227ec20]** Invalid and inefficient vfw-avi packed B frames detected**
Input #0, avi, from 'eastenders.avi':
  Metadata:
    encoder         : VirtualDubMod 1.5.10.2 (build 2540/release)
  Duration: 00:29:22.48, start: 0.000000, bitrate: 1143 kb/s
    Stream #0:0: Video: mpeg4 (Advanced Simple Profile) (XVID / 0x44495658), yuv420p, 608x336 [SAR 1:1 DAR 38:21], 25 tbr, 25 tbn, 25 tbc
    Stream #0:1: Audio: mp3 (U[0][0][0] / 0x0055), 48000 Hz, stereo, s16, 128 kb/s
[buffer @ 0x2279100] w:608 h:336 pixfmt:yuv420p tb:1/1000000 sar:1/1 sws_param:
[libx264 @ 0x2292c60] using SAR=1/1
[libx264 @ 0x2292c60] using cpu capabilities: MMX2 SSE2Fast SSSE3 FastShuffle SSE4.1 Cache64
[libx264 @ 0x2292c60] profile High, level 2.2
[libx264 @ 0x2292c60] 264 - core 119 r2106 07efeb4 - H.264/MPEG-4 AVC codec - Copyleft 2003-2011 - http://www.videolan.org/x264.html - options: cabac=1 ref=5 deblock=1:0:0 analyse=0x3:0x113 me=umh subme=8 psy=1 psy_rd=1.00:0.00 mixed_ref=1 me_range=16 chroma_me=1 trellis=1 8x8dct=1 cqm=0 deadzone=21,11 fast_pskip=1 chroma_qp_offset=-2 threads=3 sliced_threads=0 nr=0 decimate=1 interlaced=0 bluray_compat=0 constrained_intra=0 bframes=3 b_pyramid=2 b_adapt=2 b_bias=0 direct=3 weightb=1 open_gop=0 weightp=2 keyint=250 keyint_min=25 scenecut=40 intra_refresh=0 rc_lookahead=50 rc=crf mbtree=1 crf=22.0 qcomp=0.60 qpmin=0 qpmax=69 qpstep=4 ip_ratio=1.40 aq=1:1.00
Output #0, mp4, to 'output.mp4':
  Metadata:
    encoder         : Lavf53.21.0
    Stream #0:0: Video: h264 (![0][0][0] / 0x0021), yuv420p, 608x336 [SAR 1:1 DAR 38:21], q=-1--1, 25 tbn, 25 tbc
    Stream #0:1: Audio: aac (@[0][0][0] / 0x0040), 48000 Hz, stereo, s16, 128 kb/s
Stream mapping:
  Stream #0:0 -> #0:0 (mpeg4 -> libx264)
  Stream #0:1 -> #0:1 (mp3 -> libfaac)

```

---

### Post by FakeOutdoorsman on 2011-11-28
It's probably more or a warning than an error. Does the output look/play normally? If yes then you can ignore it.

---

### Post by chrisc200 on 2011-11-28
Yes it played OK. Some presets I used from winff failed though (still to investigate). Strange thing is it happens to all avi's I have. I am suprised nobody else has seen this issue. I read somewhere that its related to avi's created from Windows but don't know tbh

---

### Post by FakeOutdoorsman on 2011-11-28
> **chrisc200 said:**
> Some presets I used from winff failed though (still to investigate).

There is a known [WinFF "bug"](https://bugs.launchpad.net/ubuntu/+source/winff/+bug/874693) where your WinFF preset file in your home directory is not replaced with the newer presets when you upgrade WinFF (such as upgrading from Ubuntu 11.04 to 11.10).

So the first thing to try is to rename your preset file:
```
mv ~/.winff/presets.xml{,.old}
```
Now when you start WinFF it should make a new and correct preset file.

**Edit:** I just noticed that you compiled FFmpeg. I'm not sure how up to date WinFF is with current FFmpeg. If you want to use WinFF then I recommend you use ffmpeg from the repository instead.

---

