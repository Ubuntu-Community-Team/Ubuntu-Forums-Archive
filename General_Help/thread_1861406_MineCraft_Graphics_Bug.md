---
title: "MineCraft Graphics Bug"
date: 2011-10-15
forum: General Help
---

### Post by kkeller on 2011-10-15
So, I'm experiencing some weird graphics glitches when I play Minecraft on my computer with Ubuntu 11.10. The glitch is that there are some transparent "ants" all over the place. Here is a video.

[Video]("http://www.youtube.com/watch?v=AswWL4b6iTw")

And these are the graphics hardware and drivers:

```

konstantin@konstantin-ThinkPad-X220:~$ lspci | grep VGA && glxinfo | grep -w 'direct\|OpenGL'
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
direct rendering: Yes
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile x86/MMX/SSE2
OpenGL version string: 2.1 Mesa 7.11
OpenGL shading language version string: 1.20
OpenGL extensions:

```

Anyone have any ideas to why this is happening?

---

### Post by kkeller on 2011-10-15
Nobody?

---

### Post by kkeller on 2011-10-16
Nobody knows ANYTHING about this? Really?

---

### Post by __FrontSide__ on 2011-10-17
Since i've updated to Minecraft 1.8.1 i get the same bug. 
As far as i know it is due to "forced AntiAliasing" which is set at the graphics card.
Unfortunately i don't know how to turn it off....

---

### Post by kkeller on 2011-10-17
> **__FrontSide__ said:**
> Since i've updated to Minecraft 1.8.1 i get the same bug. 
As far as i know it is due to "forced AntiAliasing" which is set at the graphics card.
Unfortunately i don't know how to turn it off....

That sucks. There should be an option to turn it off/on.

---

### Post by crunchytheory on 2011-10-20
Glad I'm not the only one.

Knowing that it's related to forced Anti-aliasing is a good start, though.

---

### Post by kkeller on 2011-10-22
> **crunchytheory said:**
> Glad I'm not the only one.

Knowing that it's related to forced Anti-aliasing is a good start, though.

That, Is true.

---

### Post by Thartinblue on 2011-10-29
Same thing for me. I've got a new laptop with an Intel HD Graphics Sandy Bridge - 3000 and when starting minecraft, I have the same graphical problems. I used to play Minecraft under  Ubuntu 8.04 with a basic graphic card and all was good. Does anyone know if there is such problems with Ubuntu 11.04 for an Intel graphic card?

---

### Post by __FrontSide__ on 2011-11-03
> 
Same thing for me. I've got a new laptop with an Intel HD Graphics Sandy  Bridge - 3000 and when starting minecraft, I have the same graphical  problems. I used to play Minecraft under  Ubuntu 8.04 with a basic  graphic card and all was good. 


Ok, so all of us work with Sandybridge technologie maybe that's a hint.

> 
Does anyone know if there is such  problems with Ubuntu 11.04 for an Intel graphic card? 	


I use Ubuntu 11.10 with an Intel Graphic Card, so ......

---

### Post by hydroxph on 2011-11-03
Mine doesn't work either, Classic and Alpha. On my old PC though.

---

### Post by petehall on 2011-11-23
I think that this [bug report](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/882349) relates to your problem.

Pete

---

### Post by oldtimer7777 on 2011-11-23
> **petehall said:**
> I think that this [bug report]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/882349") relates to your problem.

Pete

Don't use *Compiz*  while playing games on Ubuntu....

---

### Post by petehall on 2011-11-24
> **oldtimer7777 said:**
> Don't use *Compiz*  while playing games on Ubuntu....

Using Xubuntu 11.10, so no Compiz.

Pete

---

### Post by Elktro on 2011-11-28
I have the very same problem. I am using Ubuntu 11.10 on ThinkPad L420 with Sandybrige.

I have tried to use i915.modeset=0 and 1 option on grub without any luck. Interestingly when I have Minecraft running on background also other windows on the desktop suffer from strange graphics glitches.

If any one has a workaround, please, tell us.

---

### Post by __FrontSide__ on 2012-01-23
Ok. Since i've updated to Version 1.1 the glitch is gone (for the most part).
There are still some small graphic issues though. 

What about you?

---

### Post by pbrane on 2012-01-23
> **petehall said:**
> Using Xubuntu 11.10, so no Compiz.

Pete
Make sure your compositor is turned off. I play minecraft with no problems on Xubuntu 11.10. I do have to turn off the compositor in the settings editor under xfwm4 -> general -> use_compositing. It seems to be any compositor not just compiz. I have issues on 10.04 with Metacity compositor as well.

I have an nVidia graphics card so the part about the 'marching ants' is not relevant for me.

---

