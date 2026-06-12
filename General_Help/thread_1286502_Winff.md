---
title: "Winff"
date: 2009-10-09
forum: General Help
---

### Post by note32 on 2009-10-09
does winff convert AVI to MP4?

---

### Post by OpenGuard on 2009-10-09
As long as ffmpeg can do it ( and it can ), yes.

---

### Post by note32 on 2009-10-09
well i always get this


--enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Aug 26 2009 09:45:50, gcc: 4.4.1
[NULL @ 0xa051da0]Invalid and inefficient vfw-avi packed B frames detected

Seems stream 0 codec frame rate differs from container frame rate: 29.98 (65535/2186) -> 29.97 (30000/1001)
Input #0, avi, from '/home/zach/Desktop/manhattan_love_story_ep11_sd[sars].avi':
  Duration: 00:46:01.46, start: 0.000000, bitrate: 1365 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 704x396 [PAR 1:1 DAR 16:9], 29.97 tbr, 29.97 tbn, 29.98 tbc
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, s16, 128 kb/s
Unknown encoder 'libx264'
Press Enter to Continue


and then i hit enter and nothing happens?

---

### Post by OpenGuard on 2009-10-09
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095) ( read the part about x264 ).

---

### Post by note32 on 2009-10-09
ok so i just got done doing what the x264 tutorial said to do and now i get this when i click convert win could not find FFplay

---

### Post by Lampi on 2009-10-09
what does "which ffplay" report?

if it's "/usr/local/bin/ffplay" you forgot "configure --prefix=/usr" - so ffmpeg moved from /usr to /usr/local/bin

then you need to change the path in winff (>settings>linux)

---

### Post by bigpond on 2009-11-07
> **Lampi said:**
> what does "which ffplay" report?

if it's "/usr/local/bin/ffplay" you forgot "configure --prefix=/usr" - so ffmpeg moved from /usr to /usr/local/bin

then you need to change the path in winff (>settings>linux)

mine says /usr/local/bin/ffplay

so what should be there instead?

---

### Post by Lampi on 2009-11-13
> **bigpond said:**
> mine says /usr/local/bin/ffplay

so what should be there instead?
I told 'ya - in WINFF acces the Edit menu > WINFF Preferences > Linux > change the ffmpeg path from /usr/bin/ffmpeg to /usr/local/bin/ffmpeg, same goes for ffplay

---

### Post by FakeOutdoorsman on 2009-11-13
> **OpenGuard said:**
> [http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095) ( read the part about x264 ).

An another, arguably easier, option is mentioned here:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in WinFF](http://ubuntuforums.org/showpost.php?p=8298012&postcount=20)

> **note32 said:**
> ok so i just got done doing what the x264 tutorial said to do and now i get this when i click convert win could not find FFplay

This is a known bug in WinFF.  I notified the developers and a fix is scheduled for the next release:

[Issue 56: Add /usr/local/bin for FFplay executable search](http://code.google.com/p/winff/issues/detail?id=56)

---

### Post by FakeOutdoorsman on 2009-11-13
> **Lampi said:**
> what does "which ffplay" report?

if it's "/usr/local/bin/ffplay" you forgot "configure --prefix=/usr" - so ffmpeg moved from /usr to /usr/local/bin

then you need to change the path in winff (>settings>linux)

Adding *--prefix=/usr* is not recommended.  This directory is usually reserved for official repository packages.  If no prefix is declared, compiled packages should automatically go into */usr/local* to prevent conflicts with the repository versions.  This allows you to have a repository and compiled version of the same package and can be useful to satisfy dependencies of other repository packages.

---

### Post by oldHat on 2011-10-02
> **Lampi said:**
> I told 'ya - in WINFF acces the Edit menu > WINFF Preferences > Linux > change the ffmpeg path from /usr/bin/ffmpeg to /usr/local/bin/ffmpeg, same goes for ffplay

Yep, I just ran into the same thing.

The message is deceptive.  If the path to ffplay is correct, then the problem is probably the path to ffmpeg.

Like the man said, once you fix that, you should be good to go.

---

### Post by oldos2er on 2011-10-02
Closed, necromancy.

---

