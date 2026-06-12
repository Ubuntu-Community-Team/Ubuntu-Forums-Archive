---
title: "Graphics Drivers"
date: 2010-07-22
forum: General Help
---

### Post by ChuckyZ28 on 2010-07-22
Ok I have a Foxconn R10-G3 Bare bones PC, the main issue I am having is when even I try and run light 3d games I cant do it. It gives me a message saying ubuntu is running in low graphics mode. According to the website it is direct x 9 compatible. I am not trying to run Crysis or anything extreme like that just some of the free games on software center, and I cant run any of them. In fact the only game I can consistently run is GENX LOL anyone have any suggestions what I can do. 

System Specs
 Intel® Celeron E3300
Integrated Intel® GMA 3100 graphics engine, Microsoft  Direct X 9 compliant
1 Gig of ram

---

### Post by bigfatgooglefat on 2010-07-22
It sounds like your setup doesn't have the necessary drivers for 2D or 3D acceleration. Check to see if you can install the restricted drivers under Administration --> Hardware Drivers.

---

### Post by ChuckyZ28 on 2010-07-23
unfortunately I tried that before posting. It says there are no proprietary drivers for the system.

---

### Post by Surkow on 2010-07-23
There are no restricted drivers needed for a GMA 3100 (there are only open source drivers). It should work out of the box.

---

### Post by clhsharky on 2010-07-23
> ubuntu is running in low graphics mode
Vesa driver loaded and not your graphic driver.

Intel® GMA chips have terrible drivers for Linux, but they have some 2D and 3D acceleration unlike Vesa drivers.

Sharky

Your Xorg.0.log will tell your driver info.

---

### Post by khelben1979 on 2010-07-23
The intel graphics drivers is part of the Linux kernel. Newer versions might have faster graphics performance.

What version of the Linux kernel are you using?

---

