---
title: "Ubuntu 11.04 installing libsdl1.2 Problem"
date: 2011-08-13
forum: General Help
---

### Post by Gerffy on 2011-08-13
Well I ran the code ```
sudo apt-get install libsdl1.2 libsdl-image1.2 libopenal1 libsdl-ttf2.0-0
```
 and I got some errors. Here's the result of me running that code. ```
javi@Javi-Cpu:~$ sudo apt-get install libsdl1.2 libsdl-image1.2 libopenal1 libsdl-ttf2.0-0
[sudo] password for javi: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libsdl1.2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libsdl1.2debian-nas libsdl1.2debian-pulseaudio libsdl1.2debian-oss
  libsdl1.2debian-esd libsdl1.2debian-alsa libsdl1.2debian-all

E: Package 'libsdl1.2' has no installation candidate
```
Could anyone help me?

---

### Post by dino99 on 2011-08-13
is that not clear ?

" However the following packages replace it:
  libsdl1.2debian-nas libsdl1.2debian-pulseaudio libsdl1.2debian-oss
  libsdl1.2debian-esd libsdl1.2debian-alsa libsdl1.2debian-all
"

Look at synaptic descriptions

---

### Post by Gerffy on 2011-08-13
> **dino99 said:**
> is that not clear ?

" However the following packages replace it:
  libsdl1.2debian-nas libsdl1.2debian-pulseaudio libsdl1.2debian-oss
  libsdl1.2debian-esd libsdl1.2debian-alsa libsdl1.2debian-all
"

Look at synaptic descriptions
Gee sorry I'm still in learning.

---

