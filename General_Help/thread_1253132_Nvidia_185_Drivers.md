---
title: "Nvidia 185 Drivers"
date: 2009-08-29
forum: General Help
---

### Post by RedSingularity on 2009-08-29
Anyone know when the Nvidia 185 Drivers will be available in the repos for ubuntu?

---

### Post by RedSingularity on 2009-08-29
Nevermind.  I found some repos with the updated drivers.

---

### Post by vektsilver on 2009-08-29
> **Shadow121 said:**
> Nevermind.  I found some repos with the updated drivers.

just as a side note to anyone trying to do a fresh install with the 185 drivers from the nvidia page.  They are missing some opengl files on install that causes WINE to crash over and over.

To avoid this always install the 180 driver first that is a part of ubuntu repositories. 

once the 180 is installed ( sudo aptitude install nvidia-glx-?? )

then you can go ahead and install the 185 drivers.  The opengl drivers that i assume that are missing in the 185 are supplemented by 180 

one other reason I post this is incase anyone tries to do a fresh install with the 185 repos maybe the result is the same.

My system wont even boot into safe video mode on a clean install with my gtx 285 1GB from evga.  So I am forced to manually install the driver from outside of gnome.

---

