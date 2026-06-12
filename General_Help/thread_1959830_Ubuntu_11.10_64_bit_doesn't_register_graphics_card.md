---
title: "Ubuntu 11.10 64 bit doesn't register graphics card"
date: 2012-04-16
forum: General Help
---

### Post by raziel09 on 2012-04-16
Hi all hope someone can help with this one.

I recently built a new machine with a Asrock motherboard; as the machine has a 64 bit compatible CPU and is able to take DDR2 ram i opted to install the 64 bit Ubuntu 11.10.

The first install worked fine and booted up, i installed all the updates and left out some other hardware whilst testing it.

Now i know it is stable i wanted to add my Nvidia 7800 GS card in however although i have set the BIOS to disable onboard graphics and that the main display adapter is the PCI express slot it doesn't seem to register the new card. 

It still boots up fine and displays to the onboard graphics. I installed the [SIZE=3]ppa:ubuntu-x-swat/x-updates and[/SIZE] rebooted however it still doesn't display to the dedicated
graphics.

I have looked online on this forum and google however i cannot find any commands which will tell me if Ubuntu can even detect the graphcs

any ideas?

---

### Post by 2F4U on 2012-04-16
Did you look into /var/log/Xorg.0.log if there are errors related to the card? If the card doesn't even show-up in the log, there may be a hardware problem.

---

### Post by raziel09 on 2012-04-16
Thanks for the quick reply. I had no idea that there would be log files created for things like this. 

Had a look through and it seems very confusing at first. I can see entries for my keyboard and mouse easy enough but nothing relating to the graphics.

I assume that there will be a entry such as Nvidia 7800 GS if it did show up correctly or would it just show the drivers in use?

---

### Post by 2F4U on 2012-04-16
Somewhere buried in the output it shows this for my Intel card

```
[    17.145] (II) Module intel: vendor="X.Org Foundation"
[    17.145]     compiled for 1.11.3, module version = 2.17.0
[    17.145]     Module class: X.Org Video Driver
[    17.146]     ABI class: X.Org Video Driver, version 11.0
[    17.146] (II) LoadModule: "vesa"
[    17.146] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    17.202] (II) Module vesa: vendor="X.Org Foundation"
[    17.202]     compiled for 1.11.3, module version = 2.3.0
[    17.202]     Module class: X.Org Video Driver
[    17.202]     ABI class: X.Org Video Driver, version 11.0
[    17.202] (II) LoadModule: "fbdev"
[    17.203] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    17.209] (II) Module fbdev: vendor="X.Org Foundation"
[    17.209]     compiled for 1.11.3, module version = 0.4.2
[    17.209]     ABI class: X.Org Video Driver, version 11.0
[    17.209] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
    Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
    Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
    Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
    Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server

```

Sometimes later it attempts to load the Intel driver for my card and also shows you the options it attempts to enable for the card

```
[    17.253] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    17.253] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    17.253] (==) intel(0): RGB weight 888
[    17.253] (==) intel(0): Default visual is TrueColor
[    17.253] (II) intel(0): Integrated Graphics Chipset: Intel(R) 945GM
[    17.253] (--) intel(0): Chipset: "945GM"
[    17.253] (**) intel(0): Relaxed fencing disabled

```

There is an important line at the top of the file

```
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
```

Lines marked by (EE) are errors, so you might want to particularly look at these.

---

### Post by roelforg on 2012-04-16
Did you think about "Additional drivers"?

---

### Post by raziel09 on 2012-04-16
roelforg 

I checked additional drivers and installed all of the "newer" ones (the newest one being the 173) and rebooted each time. same issue.

2F4U
Thanks for heads up on the descriptors there - completely glanced over them but i think i'm getting the hang of how to read the log files. 

Unfortunately the only one it seems to detect is the Nvidia Geforce 7025 thats installed onboard. I will try install the graphics card into the old pc to see if it has become faulty when i moved it. 

Not sure if it helps but the new motherboard is a[SIZE=2][SIZE=1] Asrock AM2+ N68C-S UCC mATx.[/SIZE] [SIZE=1]Has anyone else used one of these boards and is it possible to install a graphics card in ubuntu?[/SIZE]
[/SIZE]

---

### Post by roelforg on 2012-04-16
> **raziel09 said:**
> roelforg 

I checked additional drivers and installed all of the "newer" ones (the newest one being the 173) and rebooted each time. same issue.

2F4U
Thanks for heads up on the descriptors there - completely glanced over them but i think i'm getting the hang of how to read the log files. 

Unfortunately the only one it seems to detect is the Nvidia Geforce 7025 thats installed onboard. I will try install the graphics card into the old pc to see if it has become faulty when i moved it. 

Not sure if it helps but the new motherboard is a[SIZE=2][SIZE=1] Asrock AM2+ N68C-S UCC mATx.[/SIZE] [SIZE=1]Has anyone else used one of these boards and is it possible to install a graphics card in ubuntu?[/SIZE]
[/SIZE]

newer not always is better.
the post-release fglrx driver doesn't work for me, for example, while the older one does.

---

