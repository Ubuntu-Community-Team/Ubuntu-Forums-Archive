---
title: "Installed 10.04 and can not get compiz to work"
date: 2010-06-24
forum: General Help
---

### Post by lsutiger on 2010-06-24
I was having a file system problem on my / folder, so I went ahead and upgraded to 10.04 from 9.04 doing a manual install. I have my / and /home folders on separate partitions. All of my files and settings seem to have carried over (Firefox bookmarks, thunderbird mail, etc.

The problem is I can not get compiz to work. My video card in the laptop is the Radeon Xpress 200MXpress.

I noticed the ATI restricted drivers are no longer available. I am able to run glxgears, so it seems ubuntu has it's own driver for accelerated graphics.
I have the compiz settings manager along with the fusion-icon installed and running. I have emerald set as the window decorator and the theme I had before chosen for the window decoration. I also have compiz selected as the window manager.

When I run 'Reload window manager' from the fusion icon menu, the emerald theme tries to load, but does not. 

When I try to run gnome-do docky, it states that I need to enable compositing.....

Please help! I am impressed with the speed of 10.04 so far! WOW!

---

### Post by lsutiger on 2010-06-24
Update: Ran compiz-check. Here's the result:```
Gathering information about your system...

 Distribution:          Ubuntu 10.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RS482 [Radeon Xpress 200M]
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

```

---

### Post by lsutiger on 2010-06-24
Update 2: Ran fusion-icon from the cli and received this:```
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
compiz (core) - Warn: Exceeded max texture size

Launching fallback window manager

```
Ok, so compiz-check says the system is up to par, but there is a bug?? HELP!

---

### Post by lsutiger on 2010-06-25
OK I found the ATI driver in the Ubuntu software center. But when I try to activate the driver or run aticonfig, it states that there is noATI video card on the system....](*,)

---

