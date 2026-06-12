---
title: "FFMPEG is not working"
date: 2011-01-11
forum: General Help
---

### Post by U2XS on 2011-01-11
I am trying to extract audio from a video that I have.  So I tried using an FFMPEG command, but it results in an error.  I know that the command is right;

[HTML]ffmpeg -i Original_video.mp4 -vn -ar 44100 -ac 2 -ab 192 -f mp3 Audio_Output.mp3
[/HTML]

But the output is still an error:


```
sergio@Sergio:~$ ffmpeg -i Original_video.mp4 -vn -ar 44100 -ac 2 -ab 192 -f mp3 Audio_Output.mp3
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

Seems stream 0 codec frame rate differs from container frame rate: 2000.00 (2000/1) -> 24.00 (24/1)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'Original_video.mp4':
  Duration: 00:03:24.06, start: 0.000000, bitrate: 1097 kb/s
    Stream #0.0(und): Video: h264, yuv420p, 1280x720, 24 tbr, 1k tbn, 2k tbc
    Stream #0.1(und): Audio: aac, 44100 Hz, stereo, s16
WARNING: The bitrate parameter is set too low. It takes bits/s as argument, not kbits/s
Output #0, mp3, to 'Audio_Output.mp3':
    Stream #0.0(und): Audio: 0x0000, 44100 Hz, stereo, s16, 0 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
Unsupported codec for output stream #0.0
```

Any ideas?

---

### Post by noah++ on 2011-01-11
```
WARNING: The bitrate parameter is set too low. It takes bits/s as argument, not kbits/s
```As the error output says, you are asking it to encode at basically 0 bits per second. Change your **192** parameter to something like **192000** and see if that works.

---

### Post by U2XS on 2011-01-11
Good call.  Though now it is complaining about the Codec.  I could have sworn that the same command used to work on this very computer.

```
sergio@Sergio:~$ ffmpeg -i video_input.mp4 -vn -ar 44100 -ac 2 -ab 192000 -f mp3 audio_output.mp3
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

Seems stream 0 codec frame rate differs from container frame rate: 2000.00 (2000/1) -> 24.00 (24/1)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'video_input.mp4':
  Duration: 00:03:24.06, start: 0.000000, bitrate: 1097 kb/s
    Stream #0.0(und): Video: h264, yuv420p, 1280x720, 24 tbr, 1k tbn, 2k tbc
    Stream #0.1(und): Audio: aac, 44100 Hz, stereo, s16
File 'audio_output.mp3' already exists. Overwrite ? [y/N] y
Output #0, mp3, to 'audio_output.mp3':
    Stream #0.0(und): Audio: 0x0000, 44100 Hz, stereo, s16, 192 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
Unsupported codec for output stream #0.0

```

---

### Post by noah++ on 2011-01-11
OK, then I am guessing you don't have restricted codecs installed. If you don't have it, and you don't mind working with stuff that's not totally FOSS, can you install the[COLOR=#000000][FONT=Times New Roman][FONT=Verdana]** libavcodec-extra-52** package?[/FONT][/FONT][/COLOR]

---

### Post by U2XS on 2011-01-11
That was an embarrassingly basic mistake...   That was it.  Thanks for the help.  :)

---

### Post by FakeOutdoorsman on 2011-01-12
> **noah++ said:**
> Change your **192** parameter to something like **192000** and see if that works.

You could also use *-ab 192k*. Another option is to use -aq instead of -ab, and when using the libmp3lame encoder *-aq 4* is equivalent to *lame -V 4*.

---

