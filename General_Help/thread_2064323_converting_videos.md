---
title: "converting videos"
date: 2012-09-29
forum: General Help
---

### Post by micahpage on 2012-09-29
HTML5 only allows a few formats where 
```
MPEG 4 files with H264 video codec and AAC audio codec
```
is one of them

What would be ffmpeg's command to convert a file to mp4, h264 video, and aac audio? Does it matter what i am coverting it from? I have tried a few different options i have found on the web. such as:
```
sudo ffmpeg -i megadeth.mpg -vcodec mpeg4 -acodec aac megadeth.mp4

```
but it corrupted the output file instead

---

### Post by spaceshipguy on 2012-09-29
Looks like MP4 is the format to choose, according to these people. [http://www.longtailvideo.com/html5#media_formats](http://www.longtailvideo.com/html5#media_formats)

You might be missing a codec - [https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide) 
this guide claims to get ffmpeg installed with all the useful codecs (Ihaven't tried it, last time I used ffmpeg I was on an older version of Ubuntu and followed a guide on this page [http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)  to get the codecs I needed)

---

### Post by micahpage on 2012-09-30
I did use your suggestions, deleted and recompiled all that, and then reran the test to see if the last command on my post worked, and it did not. 

So I am not sure as if it is an incorrect argument that I am giving to ffmpeg or what.


this is the actual ouptut that i get
```
metulburr@ubuntu:~/Videos$ sudo ffmpeg -i megadeth.mpg -vcodec mpeg4 -acodec aac megadeth.mp4
[sudo] password for metulburr: 
ffmpeg version 0.8.3-4:0.8.3-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Jun 12 2012 16:52:09 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
[mpeg @ 0x11869c0] max_analyze_duration reached
Input #0, mpeg, from 'megadeth.mpg':
  Duration: 00:04:30.00, start: 0.340078, bitrate: 1396 kb/s
    Stream #0.0[0x1e0]: Video: mpeg1video, yuv420p, 352x240 [PAR 200:219 DAR 880:657], 1150 kb/s, 29.97 fps, 29.97 tbr, 90k tbn, 29.97 tbc
    Stream #0.1[0x1c0]: Audio: mp2, 44100 Hz, stereo, s16, 224 kb/s
[buffer @ 0x118efa0] w:352 h:240 pixfmt:yuv420p
encoder 'aac' is experimental and might produce bad results.
Add '-strict experimental' if you want to use it.
Or use the non experimental encoder 'libvo_aacenc'.

```

---

### Post by T.J. on 2012-09-30
Rather than use ffmpeg directly, the easiest way by far to convert video in Ubuntu is to install and use "arista", available in the software center, or via a command line:

sudo apt-get install arista

Not that I'm a lawyer and it depends on your home country, but h264/MP4 is free only for nonprofit, personal use.  If you intend to charge anything for access, you are required to pay a streaming fee.

Many people would recommend WebM instead and I'd agree, but Microsoft does not support WebM natively, so if you have a lot of Internet Explorer users, then MP4 is probably the best choice.

---

### Post by micahpage on 2012-09-30
OK I got it to work, I had to add '-strict experimental'
to the argument for aac audio

so my final result was
```
$ sudo ffmpeg -i megadeth2.mpg -vcodec libx264 -acodec aac -strict experimental megadeth3.mp4

```

---

