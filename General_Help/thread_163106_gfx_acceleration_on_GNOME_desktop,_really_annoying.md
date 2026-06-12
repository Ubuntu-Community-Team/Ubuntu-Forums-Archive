---
title: "gfx acceleration on GNOME desktop, really annoying"
date: 2006-04-20
forum: General Help
---

### Post by nic886 on 2006-04-20
ive just installed ubuntu 5.10 and downloaded the drivers for my nvidia geforce FX card using synaptic. the problem is that although full-screen openGL games, screensavers and apps work fully accelerated, ones in a window in GNOME have no acceleration and the entire desktop is very slow and sluggish. it seemed better when i was using just the open-source no acceleration drivers (on the desktop). apps like glxgears and celestia running in window mode have no acceleration. this is a real problem, could someone plz tell me whats goin on and how to accelerate my desktop. :confused:

---

### Post by bjourne on 2006-04-20
The first step, as always, is to check the file /etc/X11/xorg.conf. Do you have a section that looks like this:

```

Section "Module"
       Load    "GLcore"
       Load    "dri"
       Load    "extmod"
       Load    "freetype"
       Load    "glx"
EndSection

```

Ensure that Load "dri" and Load "GLcore" is there.

---

### Post by nic886 on 2006-04-20
yes all the modules are there and i still dont have opengl acceleration on the desktop. full screen apps work fine. ](*,)

---

### Post by PriceChild on 2006-04-20
Have you tried following this post exactly:

[http://ubuntuforums.org/showthread.php?t=75074](http://ubuntuforums.org/showthread.php?t=75074)

---

