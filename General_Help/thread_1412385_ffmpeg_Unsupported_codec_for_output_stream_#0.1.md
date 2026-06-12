---
title: "ffmpeg Unsupported codec for output stream #0.1"
date: 2010-02-21
forum: General Help
---

### Post by amsterdamharu on 2010-02-21
I know, this has been asked 465 times before (googled it) but after 2 hours reading old posts there was nothing in there that actually worked (as in encode my file).

Need to encode a file so I can test a mobile phone's ability to play 3gp files.

ffmpeg Unsupported codec for output stream #0.1

```
ffmpeg -i in.avi -s 176x144 -vcodec h263 -r 25 -b 200 -ab 64 -acodec mp3 -ab 128k -t 120 output.3gp

```
Got the package from Medibuntu

The package properties say:
> This package is built with the "risky" option, to enable mp3/mp4/h264/amr
support. Therefore, it is in Medibuntu as it might violate patents.

Output form ffmpeg -formats | grep mp3

```
ffmpeg -formats | grep mp3FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 17 2009 21:37:49, gcc: 4.2.4 (Ubuntu 4.2.4-1ubuntu3)
 DE mp3             MPEG audio layer 3
 D A    mp3
 D A    mp3adu
 D A    mp3on4

```

```
ffmpeg -i in.avi -s 176x144 -vcodec h263 -r 25 -b 200 -ab 64 -acodec copy -t 120 output.3gp

```This works but there is no audio, the original has audio but the output has nothing (in vlc audio track 1 is completely muted).

Would like to get this done in avidemux but that one doesn't encode anything workable either (no audio no video in the result after messing with it for about 2 hours)

---

### Post by amsterdamharu on 2010-02-21
After noticing the update manager wanted to do some updates and run the command again after the updates it worked. Now to see if the phone can play.

---

