---
title: "Radeon RV200 QW [Radeon 7500] video card display issue"
date: 2009-09-07
forum: General Help
---

### Post by Valkea on 2009-09-07
I'm mostly a novice Ubuntu user, still trying to learn most of this stuff so some advice would really be appreciated.  

I just picked up a new system with the Radeon RV200 QW card and the only resolution I can get is 640x480.  From what I have read, the Radeon 7500 doesn't work with Linux.  This is working but the resolution is horrible.  Any ideas?

---

### Post by Astinsan on 2009-11-20
The Radeon 7000-7500 uses DDC for monitor data probes. This will usually only return one resolution. You just need to set the option NoDDC under the device area of xorg.conf. Here is a doc that will help walk your way through it.  [http://www.lucidtips.com/2008/05/24/fix-screen-resolution-in-ubuntu-with-ati-radeon-mobility-7500/](http://www.lucidtips.com/2008/05/24/fix-screen-resolution-in-ubuntu-with-ati-radeon-mobility-7500/)


Hope that helps

---

### Post by gradinaruvasile on 2009-11-20
Well i have a laptop with 7500 mobility card and it is working perfectly (Ubuntu 8.10 though). Do not install drivers for it, they are included in the kernel. The ones u can install (from Atis site) are not for this card.

---

