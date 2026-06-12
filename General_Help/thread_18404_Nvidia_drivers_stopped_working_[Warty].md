---
title: "Nvidia drivers stopped working [Warty]"
date: 2005-03-06
forum: General Help
---

### Post by Leif on 2005-03-06
Yesterday when I shut down my computer, everything was working fine. Today when I booted, I found out that my nvidia drivers don't work, so I had to switch to nv. I've tried reinstalling them, but that doesn't sort out the problem. they are definitely there :

```
$ dpkg -l | grep nvidia
ii  nvidia-glx     1.0.6111-1ubun NVIDIA binary XFree86 4.x driver
ii  nvidia-kernel- 1.0.6111+1ubun NVIDIA binary kernel module common files
ii  nvidia-setting 1.0-3ubuntu1   Tool of configuring the NVIDIA graphics driv
``` 

Everytime I start to feel cocky about having my system setup the way I want it, something like this comes along  :)  I'd appreciate any help on how one figures this out.

---

### Post by Leif on 2005-03-27
Found my answer in another thread. If you install kernel linux-image-x, you also need to install linux-restricted-modules-x, or nvidia doesn't work.

---

