---
title: "Ubuntu 9.10 64bit will not recognize raid 5 ntfs volume"
date: 2010-02-12
forum: General Help
---

### Post by jlwilliams3rd on 2010-02-12
I have a raid 5 array formatted with ntfs; My Ubuntu OS is not able to recognize the raid 5 array but my windows 7 OS can. I had this working before when I installed ubuntu via wubi but now since i installed it as a dual boot OS I am having issues trying to mount this raid 5 volume. So far i have tried reinstalling the dmraid, ntfs config manager, and storage device manager however nothing seems to help me recognize my raid 5 array. I am very new to linux but love learning the OS, please be descriptive as possible with any suggestions. 
 
P5N32 E-SLI PLUS MOTHERBOARD: RAID 5 ARRAY NTFS with NVIDIA's raid chipset that comes built in with motherboard.
 
Thanks

---

### Post by falconindy on 2010-02-12
What you have is not RAID, but what is lovingly referred to as Fakeraid. The NVidia chipsets in particular are notorious for having flaky support on Linux.

The only foolproof solutions are to:
a) Use a real RAID controller
b) Convert to software RAID (but this means Windows won't read it)

---

