---
title: "Radeon 9600 Pro OpenGL hardlock"
date: 2006-04-25
forum: General Help
---

### Post by Runefox on 2006-04-25
I've recently been having some great difficulty with my 9600 Pro and some OpenGL games - Such as America's Army and scorched3D (surprisingly, Tux Racer is not affected) - Causing, without fail, hard lockups requiring me to reset the computer. In America's Army, for example, I load up a training map to test, and within the first second of the 3D scene being rendered, it hardlocks. Numlock doesn't respond, CTRL-ALT-BackSp doesn't respond, nothing but a hard reset.

I'm using the latest ATi drivers, and acceleration is otherwise working fine, so I'm at a loss as to why this is happening. I've checked my xorg.conf a number of times, but I can't see anything wrong with it, and it was all working fine just a few days ago. I'm pretty sure that it's OpenGL that's doing it, because scorched3d lasts a lot longer before locking than America's Army does. But again, strangely enough, PlanetPenguin Racer and XScreensaver work fine.

fglrxinfo displays the following:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 2.0.5755 (8.24.8)

My xorg.conf can be found [here](http://runefox.net/anthonius/xorg.conf). Note that I've tried without FSAA and with the Internal AGP GART as well, and it makes no difference.

I'm running Breezy 5.10 (i686-SMP kernel) on a P4 3.0E, 512MB DDR400 RAM, board is an Asus P4P800 SE. No overclocking and hardware monitor in the BIOS reports an acceptable temperature for a Prescott (~50*C).

---

### Post by mirak63 on 2006-05-01
sam problem with 9600 pro and nforce2

---

### Post by mirak63 on 2006-05-03
the solution is to rebuild the kernel without ati radeon support.
You need also to build fglrx.

[http://www.ubuntuforums.org/showthread.php?t=169509](http://www.ubuntuforums.org/showthread.php?t=169509)

---

