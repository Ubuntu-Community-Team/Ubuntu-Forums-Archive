---
title: "Ubuntu + VLC + FFMPEG"
date: 2009-10-11
forum: General Help
---

### Post by praveenmarkandu on 2009-10-11
hi, im trying to transcode a certain flv file to an mp3, stripping away the video and just keeping the audio. I am pretty damn sure i can do this in VLC in windows, but in Ubuntu, FFMPEG and VLC dont seem to play nicely together.

```
Streaming / Transcoding failed:
It seems your FFMPEG (libavcodec) installation lacks the following encoder:
MPEG Audio layer 1/2/3.
If you don't know how to fix this, ask for support from your distribution.

This is not an error inside VLC media player.
Do not contact the VideoLAN project about this issue.

```

this is the output i get when i try to encode it. i have the ffmpeg libraries installed so i'm not sure what the problem is. i did it via synaptic package manager. is encoding available through this way or do i have to build it from source?

---

### Post by Vaphell on 2009-10-11
ffmpeg -i /path/to/video.flv /path/to/song.mp3

[http://ubuntuforums.org/showthread.php?t=705990&page=2](http://ubuntuforums.org/showthread.php?t=705990&page=2)

---

### Post by ajgreeny on 2009-10-11
Or **winff** if you must have a gui.

---

### Post by praveenmarkandu on 2009-10-11
> **Vaphell said:**
> ffmpeg -i /path/to/video.flv /path/to/song.mp3

[http://ubuntuforums.org/showthread.php?t=705990&page=2](http://ubuntuforums.org/showthread.php?t=705990&page=2)

this is the output i ge when i try to run it.

```
praveen@praveen:/$ ffmpeg -i ~/Downloads/John\ Mayer\ -\ Hummingbird.flv ~/Desktop/hum.mp3
FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Aug 26 2009 09:45:50, gcc: 4.4.1

Seems stream 0 codec frame rate differs from container frame rate: 2000.00 (2000/1) -> 25.00 (25/1)
Input #0, flv, from '/home/praveen/Downloads/John Mayer - Hummingbird.flv':
  Duration: 00:05:59.95, start: 0.000000, bitrate: 85 kb/s
    Stream #0.0: Video: h264, yuv420p, 320x240 [PAR 1:1 DAR 4:3], 85 kb/s, 25 tbr, 1k tbn, 2k tbc
    Stream #0.1: Audio: aac, 22050 Hz, stereo, s16
Output #0, mp3, to '/home/praveen/Desktop/hum.mp3':
    Stream #0.0: Audio: 0x0000, 22050 Hz, stereo, s16, 64 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
Unsupported codec for output stream #0.0
praveen@praveen:/$ 

```

---

### Post by FakeOutdoorsman on 2009-10-11
> **praveenmarkandu said:**
> this is the output i ge when i try to run it.
...

Yo must be using Ubuntu 9.10 Karmic Koala.  You need to enable restricted encoders in FFmpeg with the **libavcodec-extra-52** package.  Note that as of 9.10, Ubuntu has removed AAC encoding from FFmpeg, even with the **libavcodec-extra-52** package.  If you want to be able to encode to that format you will need to compile FFmpeg yourself:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

---

### Post by rb0171610 on 2009-10-11
> **FakeOutdoorsman said:**
> Yo must be using Ubuntu 9.10 Karmic Koala.  You need to enable restricted encoders in FFmpeg with the **libavcodec-extra-52** package.  Note that as of 9.10, Ubuntu has removed AAC encoding from FFmpeg, even with the **libavcodec-extra-52** package.  If you want to be able to encode to that format you will need to compile FFmpeg yourself:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

Awesome. I had experienced these problems as well but never had the time to go searching for the answer. Thanks for the info.  I used to be able to use ffmpeg to quickly encode just about anything with a script I wrote.  I think now I will have to compile it myself.  Many thanks.

---

### Post by yasir.elsharif on 2009-11-15
*sudo apt-get install libavcodec-extra-52*
and the command  
*ffmpeg -i somefile.flv somefile.mp3*
worked very fine with me, and it's very fast! Yaah

---

### Post by thelastquincy on 2010-01-16
Thanks worked for me... Happy all around...  -QUINCY

---

### Post by redbeardthesaxon on 2010-04-02
Brilliant! Solved my problem too. Thank you all!

---

### Post by petko10 on 2010-12-21
I installed the extra-52 package and VLC worked . So for me it's solved :)

---

### Post by paxh2o on 2012-05-27
> **yasir.elsharif said:**
> *sudo apt-get install libavcodec-extra-52*



thanks! :KS:KS:KS:KS:KS

---

### Post by oldos2er on 2012-05-27
Old thread closed.

---

