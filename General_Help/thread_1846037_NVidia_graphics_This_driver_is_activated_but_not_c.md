---
title: "NVidia graphics: This driver is activated but not currently in use"
date: 2011-09-18
forum: General Help
---

### Post by searchfgold6789 on 2011-09-18
Hello everyone,
My problem today is that I just noticed that, when looking under Additional Drivers, my Nvidia "NV34 [GeForce FX 5200]" GPU has not been in use for at least one release ago. To me, this is rather like the doctor telling me that my stomach has been removed at birth and everything is just an illusion! My xorg.conf is as follows:
```

Section "Device"
    Identifier    "Default Device"
    Option    "NoLogo"    "True"
EndSection


```I can activate desktop effects (most of them, anyway) with no trouble. I cannot remember if or how I installed these drivers.
At this point, I would simply like to know what is going on here, then! And how do I use these [apparently] already installed drivers. Thank you so much for your support, both now and in the past.
 - search

---

### Post by searchfgold6789 on 2011-09-18
bump

---

### Post by oldos2er on 2011-09-18
Please don't bump your post more than once in 24 hours.

Could be this bug: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/777493](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/777493)

---

### Post by searchfgold6789 on 2011-09-18
Thank you!  I will refrain from bumping more than once a day.
I will try the suggestions in the bug tracker.

---

