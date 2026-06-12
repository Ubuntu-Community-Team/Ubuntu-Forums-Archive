---
title: "How to Setup ffmpeg on ISPConfig 3 (Ubuntu 10.04 32 bit Server)"
date: 2011-06-14
forum: General Help
---

### Post by gangs1984 on 2011-06-14
Dear All,
i am a new for Ubuntu Forms recently i setup a web-server i installed ISPConfig 3. how to install ffmpeg codec and how to setup video site (i have a script MediaMAX - Media Sharing Scrip)

please tell me how to setup

---

### Post by FakeOutdoorsman on 2011-06-14
Installing FFmpeg is easy:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

---

### Post by gangs1984 on 2011-06-15
[IMG]file:///tmp/moz-screenshot.png[/IMG][IMG]file:///tmp/moz-screenshot-1.png[/IMG]i get the following error

root@ganeshthevar:~# apt-get install build-essential git-core checkinstall yasm texi2html libfaac-dev \ libopencore-amrnb-dev libopencore-amrwb-dev libsdl1.2-dev libtheora-dev \ libvorbis-dev libx11-dev libxfixes-dev libxvidcore-dev zliblg-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
E: Couldn't find package  libopencore-amrnb-dev
root@ganeshthevar:~#

---

### Post by FakeOutdoorsman on 2011-06-15
For what you're trying to do I recommend **Option C: Medibuntu** from the link in my previous post.

---

