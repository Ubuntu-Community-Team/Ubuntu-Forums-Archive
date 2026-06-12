---
title: "Urgent Help For Ati Drivers"
date: 2006-03-04
forum: General Help
---

### Post by acankat on 2006-03-04
[http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584)

I am succesfully installing the ati drivers by following this thread step by step, after first reboot everything seems great, fglrxinfo says something like that, and 3d apps work great!;

$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro
OpenGL version string: 1.3.5272 (X4.3.0-8.16.20)

but when I shut down the computer and start it again this mesa thing come back again;

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

that happens all the time.


That is the same in both 64bit and 32bit versions.

there is something in xorg.0.log file like that:

(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(

Need urgent help, please.

---

