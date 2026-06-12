---
title: "Warning:  Kernal 2.6.31.31"
date: 2011-05-14
forum: General Help
---

### Post by Jerry N on 2011-05-14
**[SIZE="3"]BEWARE[/SIZE]**

In Ubuntu 10.04, after Kernal 2.6.31.21 got updated to 2.6.31.31 the Nvidia 260.19.21 drivers for my new GT 430 video board were no longer properly recognized.  Only low resolution was available.  Booting with the 2.6.31.21 kernal still works just fine. 

Jerry

---

### Post by ajgreeny on 2011-05-14
This is normal after a kernel upgrade.  Just install the nvidia drivers again while running the new kernel and you should be OK.

---

### Post by Jerry N on 2011-05-14
> **ajgreeny said:**
> This is normal after a kernel upgrade.  Just install the nvidia drivers again while running the new kernel and you should be OK.

I haven't tried re-installing the drivers yet but I have found that installing Nvidia 260.xx or 270.xx drivers for a GT 430 card to be a rather "iffy" proposition.  I have been trying to come up with an approach that works the same every time.  Fortunately, the computer I use for my Linux experiments has removable drive trays and I have several drives.

---

### Post by Wim Sturkenboom on 2011-05-14
You're lucky ;) At least you still can see something on the screen. Mine goes black after kernel update :( And I have to reinstall the driver. Video card is some NVidia 8400.

---

### Post by tgm4883 on 2011-05-14
Are you guys using the proprietary drivers packaged by Ubuntu, or are you installing the drivers directly from NVidia? I've never had an issue upgrading my machine. I have an 8500GT on my desktop, an onboard 6200 on my mythtv backend, and an ION in my mythtv frontend.

---

### Post by Jerry N on 2011-05-14
> **tgm4883 said:**
> Are you guys using the proprietary drivers packaged by Ubuntu, or are you installing the drivers directly from NVidia? I've never had an issue upgrading my machine. I have an 8500GT on my desktop, an onboard 6200 on my mythtv backend, and an ION in my mythtv frontend.

There aren't any drivers for a GT 430 packaged with Ubuntu 10.04, at least not that I can find.

Jerry

---

### Post by Wim Sturkenboom on 2011-05-15
I installed the prop. drivers from NVidia. This was however more of an emergency measure because I ended up with black screens (and not able to switch to a console) with any driver (nouveau, drivers in the repository).
After the install of the proprietery driver, it was still like that and eventually found out that the nouveau driver was causing the problems and solved that issue (with 'nomodeset' in grub). However never changed back to an Ubuntu driver.

---

### Post by Frogs Hair on 2011-05-15
> **Wim Sturkenboom said:**
> You're lucky ;) At least you still can see something on the screen. Mine goes black after kernel update :( And I have to reinstall the driver. Video card is some NVidia 8400.

Set your updates to notify and remove the driver before the kernel update . I have the 8400 GS  and had to remove the driver when I was using 9.10 via Wubi . It is much easier to remove the driver fool around with a black screen.

---

