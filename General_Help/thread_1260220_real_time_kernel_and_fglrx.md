---
title: "real time kernel and fglrx"
date: 2009-09-07
forum: General Help
---

### Post by Megatron3000 on 2009-09-07
I'm trying to get the best of both worlds by having the fglrx ati driver to work on jaunty 9.04 realtime - which apparently normally does not work. I would like to have it like that because with the normal driver, i get a lot of scrolling issues, dragging screens - the symptoms of low acceleration. I found this page ( [http://ubuntuforums.org/showthread.php?t=756236](http://ubuntuforums.org/showthread.php?t=756236) ) explaining me how to do that, and i adapted all the commands to the current version of the ati driver and my system: everything went correctly , as described on this page, my kernel is now recompiled with fglrx 8.640 on it. 
 
But my ati driver does not work, i still have very slowly scrolling windows (in firefox for example), and when i try to enable desktop effects, it's impossible. amdcccle tells me the ati driver is not installed, as does my hardware drivers gui. in synaptics, everything appears to be installed though. i've ran aticonfig --initial and that seems to act normal. Does anyone know how to overcome this problem? 
 
Also, with this kernel recompiling deal, i suppose i could make my normal kernel run with the ati driver, and my realtime kernel with the standard driver? if i wouldn't manage to get the fglrx driver running in real time, that would be sort of a solution - though i would like to use the rt kernel for everything, not just for studio business. And in line with that, is there a way to have normal acceleration of graphics without the proprietary driver? Thanks!

---

### Post by Megatron3000 on 2009-09-08
does anyone have an idea?

---

