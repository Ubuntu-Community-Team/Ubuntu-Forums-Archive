---
title: "Ubuntu Won't Start After Hardware Upgrade - Too Many Connections"
date: 2011-04-25
forum: General Help
---

### Post by dragonwrenn on 2011-04-25
GNU GRUB starts up

I dual boot the latest version of Ubuntu and Windows- select Ubuntu

It says too many connections
Then shows a screen loading Ubuntu 10.10 (64-bit)
Then black screens and nothing happens

This only happened after I swapped out new hardware

My old hardware was:
motherboard- Gigabyte 790XTA-UD4
processor-   AMD Phenom II Quad Core Black at 3.4
graphics card- ATI Radeon HD 5850


The new hardware (in there now):
motherboard- an MSI 890FXA-GD70 (MS-7640)
processor- AMD Phenom II 6-Core at 3.3
graphics card- ATI Radeon HD 6970

nothing was or is overclocked

I did nothing to Ubuntu after or before installing the hardware

Thanks!

---

### Post by Mark Phelps on 2011-04-26
One distinct possibility that comes to mind is that LOTS of folks have reported serious problems with Ubuntu systems using ATI 6XXX series cards -- and you switched to one of these.

If you installed fglrx drivers for your 5xxx series card, they may not work for your 6xxx series card -- and you would have to replace them with the open-source drivers first to get a display back.

Next time you boot, press SHIFT repeatedly until you get a GRUB menu, choose the recovery option, and see if you can make progress from there.

The link below shows you how to uninstall the fglrx drivers:

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

### Post by dragonwrenn on 2011-04-30
great that was it thanks
I replaced the proprietary drivers with Mesa and had to reset the graphics config too

---

