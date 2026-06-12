---
title: "How to get rid of 3d support in nvidia cards!"
date: 2010-04-01
forum: General Help
---

### Post by PARO on 2010-04-01
Hi, I'm on Hardy with XFCE on an old computer.  It's looking good and has fancy shadows and whatnot, but then I install the nvidia drivers (through jockey) and the windows start to move real slow when I drag them around. When disabling composite in XFCE's settings things appear to be faster with the nvidia driver then the nv one, so I'd like to keep it installed, but I don't want my hardware 3d acceleration (i think ?_) to be active.  I've commented out "Load glx" in modules and set 	Option "AllowGLXWithComposite" "True"  to false, but it's still the same. Is there something else I can do to make XFCE use it's software to draw shadows and transparency rather than x and my video card?

---

### Post by johngreth on 2010-04-01
In Gnome you can go to Appearance Preferences->visual effects and disable the effects that slow it down, but I don't know if there is an xfce equivalent.

---

### Post by PARO on 2010-04-02
Yes, XFCE has a "compositor" section in settings, and i can turn that off, but I WANT the fancy shadows and effects :p ! Using the "nv" driver compositing works fine until i start running too many programs.  Using the official nvidia driver it immediatly lags window movement if compositing is enabled.  But turning it off runs smooth.  So i'd like to use XFCE's software compositing instead of XGL or OpenGL or whatever is being used when the offical drivers are in use, while maintaining the extra video ram and processing (or whatever else the card is doing with the offical drivers). Help is appreciated!

---

