---
title: "mp3 avi etc. not playing, unable to install stuff using ./configure"
date: 2005-02-22
forum: General Help
---

### Post by potaman on 2005-02-22
help!!!
i installed ubuntu on my acer travelmate 2303.
i am unable to play any mp3's on it. neither am i able to play avi's. i am also unable to use ./configure , make etc. t install things, it asks for c++ support
what should i do

---

### Post by Ste on 2005-02-22
Go to synaptic and install some compilers and things.
For your avi's and things try vlc or have a look at [this thread](http://www.ubuntuforums.org/showthread.php?t=94) 

Hope this helps.

---

### Post by kassetra on 2005-02-22
[QUOTE=Ste]Go to synaptic and install some compilers and things.
For your avi's and things try vlc or have a look at [this thread]("http://www.ubuntuforums.org/showthread.php?t=94") 

Hope this helps.[/QUOTE]

You need gcc, plus the -dev files of many libraries in order to compile.

In order to play mp3s you need (most likely) gstreamer-lame, but first you'll need to upgrade your gstreamer.

As far as movies are concerned, you'll also need to install all of the proprietary codecs.

All of the media information about how to setup your system can be found in this guide: [starter guide]("http://ubuntuguide.org/")
:)

---

