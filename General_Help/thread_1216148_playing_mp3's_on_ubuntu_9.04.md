---
title: "playing mp3's on ubuntu 9.04"
date: 2009-07-17
forum: General Help
---

### Post by MythernJenkins on 2009-07-17
i have amarok installed on my computer but im new to the linux universe and out of al the websites i have visted i cant find a way to get it to work 


any help is useful

---

### Post by cariboo on 2009-07-17
Go to Sysstem-->Administration-->Synaptic Package Manager, and search for ubuntu-restricted-extras, this meta package will install most of the audio/video codecs you need to play most media, it will also install flash, java and the mscorefonts.

---

### Post by brettg on 2009-07-18
alternatively, just cut and paste 

sudo apt-get install ubuntu-restricted-extras

into a bash console

---

### Post by mc4man on 2009-07-18
> i have amarok installed

Notwithstanding any other issues install libxine1-ffmpeg, then open amarok and you be able to play mp3's.

> im new to the linux universe

from a terminal (Applications -> Accessories -> terminal

paste this in and press enter

```
sudo apt-get install libxine1-ffmpeg
```

or search in synaptic for libxine1 and you'll see the libxine1-ffmpeg package, mark for install (right click on) and 'apply'

---

### Post by vinutux on 2009-07-18
install gstreamer-plugins-bad, gstreamer-plugins-bad-multivers, gstreamer-plugins-ugly, gstreamer-plugins-ugly-multivers from synapytic

---

