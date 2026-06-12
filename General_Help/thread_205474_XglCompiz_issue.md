---
title: "Xgl/Compiz issue"
date: 2006-06-28
forum: General Help
---

### Post by Shadix on 2006-06-28
For some reason whenever I start the XGl session (after following all the instructions in [http://wiki.cchtml.com/index.php/Xgl-Compiz-Dapper](http://wiki.cchtml.com/index.php/Xgl-Compiz-Dapper) skipping the mesa part because I could not figure out how it was relevant and [http://www.ubuntuforums.org/showthread.php?t=168618](http://www.ubuntuforums.org/showthread.php?t=168618)) 
nothing seems to work.  I don't see any of the effects (even the keyboard functions for switching workstations dont work) and when I turn on an application it's nudge in the upper lefthand corner of the screen without the bar with the closing out and minimize buttons.

The after about 30 seconds with an app open Gnome just completely locks up and I have to manually turn my PC off.

What on earth is going on and what could I check to get possible error logs?


Edit: LMAO.  I forgot to mention that I use a Radeon 9250 and have working FGLRX drivers (as far as I know, nobody told me how to check if 3D acceleration is working or what I need to support it.)

---

### Post by knn on 2006-06-28
[QUOTE=Shadix]For some reason whenever I start the XGl session (after following all the instructions in [http://wiki.cchtml.com/index.php/Xgl-Compiz-Dapper](http://wiki.cchtml.com/index.php/Xgl-Compiz-Dapper) skipping the mesa part because I could not figure out how it was relevant and [http://www.ubuntuforums.org/showthread.php?t=168618](http://www.ubuntuforums.org/showthread.php?t=168618)) 
nothing seems to work.  I don't see any of the effects (even the keyboard functions for switching workstations dont work) and when I turn on an application it's nudge in the upper lefthand corner of the screen without the bar with the closing out and minimize buttons.

The after about 30 seconds with an app open Gnome just completely locks up and I have to manually turn my PC off.

What on earth is going on and what could I check to get possible error logs?


Edit: LMAO.  I forgot to mention that I use a Radeon 9250 and have working FGLRX drivers (as far as I know, nobody told me how to check if 3D acceleration is working or what I need to support it.)[/QUOTE]

The problem is you skipped the mesa part. Xgl and Compiz require an OpenGL extension that the proprietary drivers do not yet have. Until Nvidia and Ati implement this extension in their drivers, you have to use mesa.

---

### Post by Shadix on 2006-06-30
My question is why did it tell me I had to have FGLRX and working 3D Hardware Acceleration with that to do it?

---

### Post by joshrobinson on 2006-06-30
[QUOTE=Shadix]My question is why did it tell me I had to have FGLRX and working 3D Hardware Acceleration with that to do it?[/QUOTE]

you need to have a working accelerated desktop first, with fglrxinfo displaying ati. then make sure you install mesa

---

### Post by grendelkhan on 2006-06-30
There's a couple functions that Mesa implements in software that the proprietary drivers don't have, but the proprietary drivers give you hardware accelerated OpenGL, which compiz also needs.  It's a combination of both the current proprietary drivers and Mesa that gives XGL and compiz all the cool stuff it has.

---

