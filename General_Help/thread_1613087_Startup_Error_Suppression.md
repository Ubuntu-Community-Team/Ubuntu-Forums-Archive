---
title: "Startup Error Suppression"
date: 2010-11-04
forum: General Help
---

### Post by blinksilver on 2010-11-04
A while ago I was installing an SSD into my laptop. During the process I put a small slit into the ribbon cable which connects the drive to the motherboard. Luckily the cut was restricted to the hard-reset line (Its the line that resets your drive when you hit reboot on your computer.). I say luckily because, strictly speaking, you don't really need said line unless you do soft reboot.

The upshot of this is that I have to pass a command to the kernel at startup (libata.force=nohrst) which stops the system from doing a hard reset of the drive on startup. (Apparently this is standard protocol on Unix type systems, FeeBSD and Darwin both do the same, but windows abstains from such behavior.)

The system behaves fine when one does this. However, at startup, the kernel throws an error informing the reader that the drive's hard reset failed. I would not mind this so much if it did not stop the splash from loading. Its, the very sensible, default behavior to the the splash module(I don't know its name, it was usplash ages ago, but has since changed) to show any kernel related errors instead of the Ubuntu startup screen.

My question is: Does anyone know of a kernel level or splash screen level way of suppressing this error or at least a simple way of stopping it from showing up instead of the splash screen at every startup? 

I would really like to see that splash screen instead. I knows its just a pleasantry, but it would be nice.

Much obliged.

---

### Post by blinksilver on 2010-11-04
For all those facing similar problems, installing cryptsetup does the trick. 

Also, for those who find this sort of thing important, It had no discernible impacting on startup time. I ran a stopwatch a couple times for posterity and in both cases my system took 16 seconds (after the bios had handed off) to load the desktop.

---

