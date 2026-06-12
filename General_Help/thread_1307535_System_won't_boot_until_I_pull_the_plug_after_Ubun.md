---
title: "System won't boot until I pull the plug after Ubuntu was running"
date: 2009-10-31
forum: General Help
---

### Post by spacechild on 2009-10-31
Folks,

I'm experiencing a disturbing problem on my machine. I dual-boot between Windows 7 and Ubuntu 9.10. The installation of Ubuntu went smooth, grub is working OK, nothing unusual here. BUT:

After booting and working with Ubuntu, if I want to reboot my machine, the system shuts down normally, then I get a freeze at the BIOS POST screen. I can see the Energy Star logo and two or three lines that identify my chipset, but it won't coninue from there. Sometimes I additionally get the piece of text telling me how much RAM is installed, sometimes not.

When I power-off by pressing the power button for a couple of seconds, then wait a few more seconds and turn the computer on again, it hangs at the same point.

In order to boot again, I have to physically unplug the power cord, replug it, then I can boot. It also doesn't matter if I end my Ubuntu session with "Reboot" or "Shutdown" -- once I was in Ubuntu, I have to physically unplug my system before it will boot again. When using Windows, everything works as one would expect, I can shutdown or reboot as many times as I want.

I tired several different options for the reboot= kernel parameter, but had no success. To me, it seems that some piece of hardware goes into an undefined state, causing the BIOS to hang at the POST screen. The weird thing is that not even a forced poweroff by holding the power button helps.

My machine consists of: Core2Duo E6600, Gigabyte GA-EP45-UD3LR mainboard with Intel P45 chipset, 4GB DDR2 667 (4 modules with 1 GB each), one SATA HDD, one SATA DVD burner. USB mouse and keyboard, 1 Realtek Gigabit NIC (onboard), 1 Intel Gigabit NIC (PCI card), nVidia 9600 PCI-E.

Does anyone have any idea what the problem could be or where to look in order to further investigate this?

Thanks
SC

---

### Post by grandtoubab on 2009-10-31
kind of Hibernate problem somewhere cause once upon a time I try the hibernate option and I can't no more boot until I unplug power

---

### Post by spacechild on 2009-10-31
If hibernation does not work that's fine for me, I don't even want to use that. But the problem also occurs if I shutdown completely, and later turn the computer back on, and it has not been completely unplugged in the meantime.

I'm currently downloading a Knoppix live CD to see if it also produces this problem. Still hoping it can be fixed using a kernel parameter or something...

---

### Post by JBAlaska on 2009-10-31
Guessing it may be in the BIOS power saving options (energy star), try disabling those.

---

### Post by spacechild on 2009-10-31
I will fiddle about the power saving options after my Knoppix download finishes. I have a slow connection though, it will take about two hours to download a 700 MB ISO.

---

### Post by spacechild on 2009-10-31
With Knoppix 02/2009 I can shutdown and reboot just fine, without any POST freezes. I haven't changed any BIOS settings yet, so I assume there must be something in the default configuration of Ubuntu 9.10 that brings my machine to this strange state. Knoppix uses this kernel and parameters:

knoppix@Microknoppix:~$ uname -a
Linux Microknoppix 2.6.28.4 #8 SMP PREEMPT Mon Feb 9 14:33:28 CET 2009 i686 GNU/Linux
knoppix@Microknoppix:~$ cat /proc/cmdline
ramdisk_size=100000 lang=de vt.default_utf8=0 apm=power-off vga=791 initrd=minirt.gz nomce quiet loglevel=0 nolapic_timer BOOT_IMAGE=linux

I'll dig through my mainbaord's manual later today to see if I find any suspicious BIOS settings...

---

### Post by grandtoubab on 2009-10-31
what about 
System -> Preferences -> Energy Manager (I am french so I translate the menu but that is the idea)

Try never sleep option

---

### Post by spacechild on 2009-10-31
Thanks for the pointer, but unfortunately the energy settings were already configured to "never sleep".

I also tried using the noacpi kernel parameter, but that did not change anything either.

I'm afraid I'm running out of ideas. I'm thinking about compiling my own kernel, but I'm not very eager to do that.

---

### Post by spacechild on 2009-11-01
I was finally able to solve this problem by going into the BIOS setup and disabling "Legacy USB storage detect" in the "Integrated peripherals" panel.

I really wonder what exactly was going on that this option could cause the observed behaviour, though.

---

### Post by grandtoubab on 2009-11-04
> **spacechild said:**
> I was finally able to solve this problem by going into the BIOS setup and disabling "Legacy USB storage detect" in the "Integrated peripherals" panel.

I really wonder what exactly was going on that this option could cause the observed behaviour, though.

Maybe you have an equipment plugged on usb as printer??

---

