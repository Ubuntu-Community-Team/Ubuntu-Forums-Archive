---
title: "Large black rectangles on tabbed windows"
date: 2010-10-14
forum: General Help
---

### Post by geostar1024 on 2010-10-14
Recently, I've run into a rather interesting but also quite annoying instance of graphical corruption: a large black rectangle covering all or part of the window various running applications.  What makes it interesting is that this graphical corruption only seems to occur in applications that have at least 2 tabs open.  I've confirmed that it happens in pidgin, nautilus, gnome-terminal, and gedit; the latter 3 are shown in the attached screenshot.

Clearly, it has something to do with my graphics driver.  I'm currently using the open source radeon driver in ubuntu 10.04 with a Radeon 9800XT.  I'm not sure what logs and system information would be appropriate to post, so please advise.

---

### Post by geostar1024 on 2010-10-29
*bump* Nothing at all, eh?

---

### Post by geostar1024 on 2010-11-12
It looks like the root cause of this odd behavior was the fact that all graphics were being drawn using the software rasterizer (so my graphics card wasn't being used at all).  This situation occurred because I added "radeon.modeset=0" to my kernel boot line in order to get around a soft cpu lockup caused by plymouth.  My solution was to upgrade to 10.10, which apparently solved the issue with plymouth and thus allowed booting with the graphics card enabled.  The upshot is that all the black rectangles are gone!

Conclusions:
-Ubuntu 10.04's plymouth has a cpu soft lockup bug that has some connection to the system's graphics card being enabled.
-adding "radeon.modeset=0" to the kernel line disables 3D acceleration for ATI graphics cards using the open source radeon driver, and allows a system suffering from the plymouth soft lockup bug to boot.
-Ubuntu 10.10's plymouth is apparently free of the soft lockup bug.

---

### Post by kommissario on 2011-03-25
I have the same problem using Ubuntu 10.10 Satanic Edition on Asus K50c Laptop - for sure the responsibility is of the drivers of the graphic card which I had to install separetely, this laptop is crap for linux! Any idea on how to solve this?

---

