---
title: "i810 graphics card problem"
date: 2006-03-30
forum: General Help
---

### Post by ILikeLinux on 2006-03-30
Hi, 

One of my friend, a die-dard windows lover, has a new computer
with intel 845 GL chipset. I managed to convince her to try ubuntu
and installed Breezy on her computer. But the problem is that it can
get only very low resolution, 640x480  to be exact. 

I looked at wiki pages, they recommended that some package, 
915resolution should be installed and configured. I followed all 
those instructions, but nothing seems to change. 

Help required urgently to keep her trying to use ubuntu at least.

Please note that the windows (damn it) is giving the perfect 
resolution.

---

### Post by kairu0 on 2006-03-30
First, I'd double-check the xorg.conf to make sure that the resolutions are prioritized in the order that you like (a.k.a. your preferred resolution is before 640x480), and that your preferred resolution is mentioned in the color depth section that you are going to use.

Second, it could be a modeline problem. Make sure that those numbers match those in your monitor's documentation.

---

### Post by ILikeLinux on 2006-04-01
Solved!!! The problem was that the BIOS was giving only 1MB for the 
Video RAM. I had done all the things recommended in various posts.
All the modellines etc, were all fine. Still it didn't seem to matter. 

Finally I hit upon some post which said about this RAM set-up in BIOS.
Once I changed this worked like charm. To make sure that that was the
problem, I again changed the RAM allocation in BIOS and again I had
the problem. I changed back - things are fine. 

Anyway, my friend has atleast agreed to try this for a few days, hope she
likes it. Then this effort will be worthwhile.

---

