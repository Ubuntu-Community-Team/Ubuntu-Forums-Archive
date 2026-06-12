---
title: "crazy mysterious beeping on default startup, but not recovery"
date: 2009-08-03
forum: General Help
---

### Post by Kazagistar on 2009-08-03
My hardware for reference.
```
Western Digital Caviar Black WD6401AALS 640GB 7200 RPM SATA 3.0Gb/s 3.5" Internal Hard Drive
OCZ Platinum 6GB (3 x 2GB) 240-Pin DDR3 SDRAM DDR3 1600 (PC3 12800) Low Voltage Desktop Memory Model OCZ3P1600LV6GK
LG Black LG Blu-ray/HD DVD-ROM & 16X DVD±R DVD Burner SATA Model GGC-H20L
XFX PVT98GYDLU GeForce 9800 GT 512MB 256-bit GDDR3 PCI Express 2.0 x16 HDCP Ready SLI Supported Video Card
EVGA E758-TR 3-Way SLI (x16/x16/x8) LGA 1366 Intel X58 ATX Intel Motherboard
Intel Core i7 920 Nehalem 2.66GHz LGA 1366 130W Quad-Core Processor Model BX80601920
PC Power & Cooling S61EPS 610W Continuous @ 40°C EPS12V SLI Certified CrossFire Ready 80 PLUS Certified Active PFC Power
```
Yes, it is a little dangerously bleeding edge, but for a while it was working fine. But recently (past few months), I have been having a problem... whenever I boot up, no matter which kernel I boot up, part way through the startup (I think it is just after the processors are initialized or something, but it happens to fast to really tell) the system beep or whatever it is called starts beeping at a rate of about 10 beeps a second, continuously, rather erratically (it misses some beeps, but no discernible pattern). When it would normally boot GDM, the screen gets weirdly zoomed in on some text, and the beep freezes into a on tone for about 10 sec, then it resumes beeping, blanks the screen, and becomes unresponsive. If I press the power button once, it sounds like it is trying to turn off, but it does not do anything.

But here is the weird thing: when I boot my other partition (windows) there is no beeping, and if I boot Ubuntu in recovery mode, and then just press resume boot as soon as the menu comes up, there is no beeping, and my system works fine. ONLY the default Ubuntu boot options are broken and cause the beeping.

So I have been able to use my system with Ubuntu just fine, I just have to participate a bit more in the boot process to use this workaround I discovered. I was wondering if anyone could shed a bit more light on this strange problem, or give me advice on how to further debug it.

---

### Post by wojox on 2009-08-03
Blacklist the beep.

[http://ubuntuforums.org/showthread.php?t=1139234&highlight=Blacklist+beep](http://ubuntuforums.org/showthread.php?t=1139234&highlight=Blacklist+beep)

It's about half way down. Look for blacklist.

---

### Post by Kazagistar on 2009-08-03
I tried this:
> **w3wsrmn said:**
> You can unload the PC speaker module with
```
modprobe -r pcspkr
```And add the following line to **/etc/modprobe.d/blacklist.conf** to prevent the module from ever loading
```
 blacklist pcspkr
```
The beeping was exactly as before... a long, continuous stream of endless beeps, and a dysfunctional system... but only the default boot option; the "recovery option" works like a charm.

---

