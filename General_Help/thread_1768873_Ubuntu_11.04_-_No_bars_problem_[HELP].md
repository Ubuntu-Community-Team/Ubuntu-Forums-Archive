---
title: "Ubuntu 11.04 - No bars problem [HELP]"
date: 2011-05-27
forum: General Help
---

### Post by BramTerlouw on 2011-05-27
As I updated to 11.04 I first had some issues regarding the NVIDIA drivers, so I deinstalled them. There was an option for Beta 3D NVIDIA drivers, so I decided to install them instead of the other one. As a result I do not have any bars anymore. I only have the background. I can open the console but the gnome-bar won't show up.

Intel Pentium 4
2 GB DDR2 RAM
320 GB HD HITACHI
GeForce 5300 or 5200.

So it's an oldie, and no Kubuntu and puppylinux is nothing for me. I tried that. Also Ubuntu should run properly with these specs.

Could someone tell me how to get my bars back?

---

### Post by LordNeo on 2011-05-27
from terminal run nvidia-settings and check the options, maybe the bars are "outside" the screen.
Also try to run unity-launcher (or unity-2d-launcher)

---

### Post by coffeecat on 2011-05-27
> **BramTerlouw said:**
> As I updated to 11.04 I first had some issues regarding the NVIDIA drivers, so I deinstalled them.

What were the issues and which version did you install? If it was the 270 version, this wouldn't support an old card like the Geforce 5200. You'd need the 173 version.

> **BramTerlouw said:**
> There was an option for Beta 3D NVIDIA drivers

Was this the experimental package? This installs libgl1-mesa-dri-experimental which complements the open source nouveau driver (not the proprietary nvidia) to give it 3d acceleration. It is still unstable with some cards so if this is what you installed, then maybe this is the cause of your problem.

If you installed the 270 ("current") nvidia driver before, go into Additional Drivers and enable the 173 driver. This may help.

---

