---
title: "installing codecs or using new media player"
date: 2006-01-20
forum: General Help
---

### Post by njzillest on 2006-01-20
How do i install codecs for VLC player.... or is there any other good recomendations to play .mp3, .AVI, .WAV, and DVD's?


if there is how do i get it? any way to get it through apt-get or snyaptic?


...and yes im a linux n00b... windows mAster

---

### Post by earobinson on 2006-01-20
[http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-music-and-movies](http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-music-and-movies)

---

### Post by frodon on 2006-01-20
The same codecs are used for all the player, so all you have to do is to install the common codecs and all the players will work.
You can install them with synaptic, the package you may need are : w32codecs, libdvdcss2, gstreamer0.8-plugins, gstreamer0.8-lame, gstreamer0.8-ffmpeg, gstreamer0.8-faac, gstreamer0.8-faad, libxvidcore4, lame, sox, ffmpeg, mjpegtools, vorbis-tools, mpg321.
For w32codecs and libdvdcss look here : [http://www.ubuntuforums.org/showthread.php?t=78611](http://www.ubuntuforums.org/showthread.php?t=78611)

---

### Post by AgonxOC on 2006-01-20
Hello guys. I ran into this thread and I have a few questions... I followed the  link above and I did the extra repositories ( I had done this before from the terminal I thought), Once I add repositories do I need to add them everytime? Do I need to remove them once I am done for security reasons? Also I couldnt find MJPEGTOOLS and GSTREAM0.8LAME... What should I do?

Alex

---

### Post by earobinson on 2006-01-20
> Once I add repositories do I need to add them everytime?No, once you add them they are in for good, unless you reinstall ubuntu.
> Do I need to remove them once I am done for security reasons?User choice, the most secure way to run your computer is only using the offical repositorys (ones that come set up with install), But most users will not have a problem with the backports
> Also I couldnt find MJPEGTOOLS and GSTREAM0.8LAME... What should I do?They may just be missing right now, if everything runs I wouldent worrie, If something dont post and we will figure it out.

---

### Post by frodon on 2006-01-20
First to explain you a little bit more, gstreamer plugins are needed if you use the default totem player, if you use the totem-xine package (it's the same GUI but using the xine backend) you don't need them.
For the extra repository, i guess you mean the plf repository, i think you could disable it after installing w32codecs and libdvdcss2.
If you didn't find mjpegtools and gstreamer0.8-lame maybe you don't have all the repositories enabled (try to search with gstreamer as keyword before as to be sure), here is a useful link about repositories : [http://www.ubuntuforums.org/showthread.php?t=92672](http://www.ubuntuforums.org/showthread.php?t=92672)

---

