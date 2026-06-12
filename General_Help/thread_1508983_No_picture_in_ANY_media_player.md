---
title: "No picture in ANY media player"
date: 2010-06-13
forum: General Help
---

### Post by Sorseg on 2010-06-13
It happened after i installed easy-ocr from [https://help.ubuntu.com/community/OCR](https://help.ubuntu.com/community/OCR).
It reset my gnome settings and now totem/mplayer/vlc show black rectangle instead of video, sound is ok. mplayer doesn't even show any OSD activity
Tried reinstalling totem/mplayer/vlc/gstreamer/ubuntu-restricted-extras, tried changing video output in gstreamer-properties. Nothing helps.

p.s. flashplugin shows videos from youtube ok

p.p.s. [big_buck_bunny]("http://mirrorblender.top-ix.org/peach/bigbuckbunny_movies/big_buck_bunny_480p_stereo.ogg") in ogx streams ok though FF, but if i download it and play using totem same black rectangle instead of video

---

### Post by Sorseg on 2010-06-13
Solved thanx to [http://ubuntuforums.org/showthread.php?t=1316540](http://ubuntuforums.org/showthread.php?t=1316540)

> Often this means that the video-out device selected by your program will  not work on your system. This can be tested in vlc for example by going  to:

Tools --> Preferences --> Video --> Output

and selecting an alernative like 'x11 video output'.

---

