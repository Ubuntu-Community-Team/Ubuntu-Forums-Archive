---
title: "Problems with video graphics 9.10"
date: 2010-02-06
forum: General Help
---

### Post by adimoshu on 2010-02-06
Hello all,

I have a problem with my 9.10 distribution. Everything worked out very good until I wanted to improve the video performance. I have an ATI radeon x700 video card. I know there are problems with this card. I unninstalled all graphics drivers and then tried to install from the begining. After uninstalling them, I could only work in text mode. From there I tried to install agai the graphics drivers using 
     sudo apt-get install xserver-xorg
Now the problem is when it prompts me to login in the graphical mode, I enter the password, it looks like is going to login, but then the screen flickers and it shows again the login window. And it keeps doing that. I tried to change the password, but it still not working. If somebody can help me and tell me exactly how I can reinstall my video drivers and how to pass the login problem (which I'm very sure it's not related to the password)

Thanks

---

### Post by efflandt on 2010-02-06
I don't recall which ATI card I had in an older computer I gave away, but it either bounced back to login in Xubuntu 9.10 after first updates, or right after installation half loaded and froze gnome in Ubuntu 9.10.

Installing **xorg-driver-fglrx** seemed to resolve that.  Synaptic provides little details about it other than:

> Video driver for the ATI Radeon and FireGL graphics accelerators.

This package provides 2D display drivers
and hardware accelerated OpenGL.Any other computers I have run Ubuntu on with ATI or nVidia have worked fine with standard kernel and X modules.

---

