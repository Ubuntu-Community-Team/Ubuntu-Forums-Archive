---
title: "GeForce FX 5200 and AGP rate"
date: 2009-09-08
forum: General Help
---

### Post by URPradhan on 2009-09-08
Hi Friends

How can we change the default agp rate of nVidia's GeForce FX 5200 from 8X to 4X ? 
Note that: I have activated the nVidia Graphics driver 173.x through Ubuntu 9.04

I'm experiencing HARD-FREEZE on my Ubuntu box, with this card, when I'm trying to open ANY application after a fresh reboot and sometimes even if during OS installation !!! 

Thank you.

---

### Post by P4man on 2009-09-08
what makes you think AGP speed has anything to do with it?
Hard freezes can be a pain to troubleshoot, first thing to check would be if your hardware is okay. Is the machine stable under another OS (windows?)?

---

### Post by P4man on 2009-09-08
anyway to answer your question try this:

```
gksudo gedit /etc/X11/xorg.conf
```

Find the device section that describes your videocard and add:

>  Option          "AGPMode" "4"

---

### Post by URPradhan on 2009-09-08
> **P4man said:**
> what makes you think AGP speed has anything to do with it?
Hard freezes can be a pain to troubleshoot, first thing to check would be if your hardware is okay. Is the machine stable under another OS (windows?)?

Thank you for your reply.
I have tried many options with this problem with the support of other forums. And as the PC getting booted normally and freezes when I try to launch any application. That implies either there could be a setting mismatch/conflict in BIOS (as its happening across OSes) or there could be a driver issue or may be also the hardware is gone :(

But I do not think (yes ..I think) that there could be  problem with the hardware as its getting booted normally and runs as usual If I'll leave it untouched after boot. And it freezes ONLY when I try to run any application. Even I've tested the RAM with memtest86+ and checked the HDD also.

So, I'm trying my luck with this option of AGP rate resetting.

---

### Post by fragos on 2009-09-08
I had an FX5200 that worked well at 8x AGP with the 173 driver. A chip burnt so I replaced it with an FX6200 AGP that also works well with the recommended 180 driver. There are a number of vendors that build Nvidia based cards so there may be hardware differences despite using the same GPU.

---

### Post by URPradhan on 2009-09-09
> **fragos said:**
> I had an FX5200 that worked well at 8x AGP with the 173 driver. A chip burnt so I replaced it with an FX6200 AGP that also works well with the recommended 180 driver. There are a number of vendors that build Nvidia based cards so there may be hardware differences despite using the same GPU.

Thank you sir, even it seems some internal component of my AGP card has gone/burnt as all my efforts are in vain. There is nothing wrong with the driver/OS. I need to follow ur path and have to buy another card :(

---

