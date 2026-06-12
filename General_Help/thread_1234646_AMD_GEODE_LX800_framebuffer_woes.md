---
title: "AMD GEODE LX800 framebuffer woes"
date: 2009-08-08
forum: General Help
---

### Post by krauser530 on 2009-08-08
I've spent the last few days trying to get directfb applications working on an AMD GEODE LX800 system with no luck. I have the xorg-xserver-video-geode package installed and the directfb and sdl libraries installed. 

The issue seems to be that when I use ctrl+alt+number to get to a virtual console, the screen goes black. This only happens when i select a vesa mode at boot, though. Under a normal boot without a mode selected, virtual consoles work perfectly. I've used a number of different modes with no luck.

Is there a step I'm missing to get things working? Has anyone else had difficulty setting this up?

---

### Post by kerry_s on 2009-08-08
have you tried the wiki?
[http://www.directfb.org/wiki/index.php/DirectFB:HOWTOs](http://www.directfb.org/wiki/index.php/DirectFB:HOWTOs)

---

### Post by krauser530 on 2009-08-08
Yeah that was what I was using to try and get things setup. I still can't get things working. I'm guessing there's some kind of driver thats missing for my hardware, but I don't know what it would be.

---

