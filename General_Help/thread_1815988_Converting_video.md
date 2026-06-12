---
title: "Converting video"
date: 2011-08-01
forum: General Help
---

### Post by FinalShot on 2011-08-01
I've already tried Winff ( it gave me errors ) and Handbrake ( it won't let me start the encoding ), any suggestions are appreciated,

---

### Post by aeiah on 2011-08-01
they probably both rely on ffmpeg at the back end. launch both with a terminal and see what messages are produced when you try and do things.

---

### Post by 3rdalbum on 2011-08-01
> **aeiah said:**
> they probably both rely on ffmpeg at the back end. launch both with a terminal and see what messages are produced when you try and do things.

Does your system actually play the videos? If not, then it's probably a codecs issue - you will need to install all the restricted codecs. The easiest way of doing this is to add the Medibuntu repository to your system and installing the "non-free-codecs" package. [www.medibuntu.org](www.medibuntu.org) should help you there.

---

### Post by frncz on 2011-08-01
Have you tried Openshot?
Works very well for me
Mike

---

### Post by FakeOutdoorsman on 2011-08-01
> **FinalShot said:**
> I've already tried Winff ( it gave me errors )
What errors did you get? What output format do you want? What Ubuntu version are you using?

---

### Post by FinalShot on 2011-08-17
Yes VLC plays all the videos.

Openshot crashed without errors.

WinFF errors:
```

ffmpeg version N-30935-g86824c1, Copyright (c) 2000-2011 the FFmpeg developers
  built on Jun 22 2011 11:45:21 with gcc 4.4.3
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-libfaac --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libxvid --enable-x11grab --enable-libmp3lame
  libavutil    51.  9. 1 / 51.  9. 1
  libavcodec   53.  7. 0 / 53.  7. 0
  libavformat  53.  4. 0 / 53.  4. 0
  libavdevice  53.  1. 1 / 53.  1. 1
  libavfilter   2. 23. 0 /  2. 23. 0
  libswscale    2.  0. 0 /  2.  0. 0
  libpostproc  51.  2. 0 / 51.  2. 0
[matroska,webm @ 0x2467400] Estimating duration from bitrate, this may be inaccurate

Seems stream 0 codec frame rate differs from container frame rate: 47.95 (20000000/417083) -> 23.98 (24000/1001)
Input #0, matroska,webm, from '/home/scott/Desktop/test video.mkv':
  Metadata:
    title           : test video
  Duration: 00:20:56.57, start: 0.000000, bitrate: N/A
    Stream #0.0: Video: h264 (High), yuv420p, 624x352, PAR 255:254 DAR 9945:5588, 23.98 fps, 23.98 tbr, 1k tbn, 47.95 tbc (default)
    Metadata:
      title           : test video
    Stream #0.1: Audio: aac, 48000 Hz, stereo, s16 (default)
[NULL @ 0x2498e40] [Eval @ 0x7fff6510e040] Invalid chars 'b' at the end of expression '128kb'
[NULL @ 0x2498e40] Unable to parse option value "128kb"
Invalid value '128kb' for option 'ab'
Press Enter to Continue

```

Something that will work on an iPod touch so MP4. I'm running Ubuntu 10.04 64bit.

---

### Post by Duncan Williams on 2011-08-17
I have been using two programs for converting video from one format to another.
miro (very fast)
Avidemux
between these two you should be able to convert most formats.
both available from `software manager'

---

### Post by andrew.46 on 2011-08-17
> **FinalShot said:**
> 
```

[NULL @ 0x2498e40] [Eval @ 0x7fff6510e040] Invalid chars 'b' at the end of expression '128kb'
[NULL @ 0x2498e40] Unable to parse option value "128kb"
Invalid value '128kb' for option 'ab'
Press Enter to Continue

```

You have quite a new copy of FFmpeg and WinFF is using syntax suitable for an older version. Try the following single command and see if things work better:

```

mv -v ~/.winff/presets.xml ~/.winff/presets.xml_bak && \
cp -v /usr/share/winff/presets-libavcodec52-v6.xml ~/.winff/presets.xml

```

---

### Post by FinalShot on 2011-08-17
> **andrew.46 said:**
> You have quite a new copy of FFmpeg and WinFF is using syntax suitable for an older version. Try the following single command and see if things work better:

```

mv -v ~/.winff/presets.xml ~/.winff/presets.xml_bak && \
cp -v /usr/share/winff/presets-libavcodec52-v6.xml ~/.winff/presets.xml

```

When I run that I get this:
```
scott@lucid:~$ mv -v ~/.winff/presets.xml ~/.winff/presets.xml_bak && \
> cp -v /usr/share/winff/presets-libavcodec52-v6.xml ~/.winff/presets.xml
mv: cannot stat `/home/scott/.winff/presets.xml': No such file or directory
```

> **Duncan Williams said:**
> I have been using two programs for converting video from one format to another.
miro (very fast)
Avidemux
between these two you should be able to convert most formats.
both available from `software manager'

I'll try both of them.

---

### Post by andrew.46 on 2011-08-19
> **FinalShot said:**
> When I run that I get this:
```
scott@lucid:~$ mv -v ~/.winff/presets.xml ~/.winff/presets.xml_bak && \
> cp -v /usr/share/winff/presets-libavcodec52-v6.xml ~/.winff/presets.xml
mv: cannot stat `/home/scott/.winff/presets.xml': No such file or directory
```

Seems a bit odd as I expected the defaults to be in place at least. Perhaps simply move the presets in /usr/share/:

```

cp -v /usr/share/winff/presets-libavcodec52-v6.xml ~/.winff/presets.xml

```

---

### Post by jfed on 2011-08-19
I use the oldschool way, mencoder. Of course you're going to have to look threw the manual to figure out how to convert what you need properly, or you can look up a few tuts for it online.

---

