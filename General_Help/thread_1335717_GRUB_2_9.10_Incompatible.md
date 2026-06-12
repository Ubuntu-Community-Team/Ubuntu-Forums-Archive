---
title: "GRUB 2 9.10 Incompatible?"
date: 2009-11-23
forum: General Help
---

### Post by aust77 on 2009-11-23
I have bounced between 9.04 and 9.10 over the past two weeks, due to booting problems. I checked my install CD for defects, with the system citing it is fine. My problem with 9.10 is that instantly after I install, it takes around five to seven manual restarts to successfully boots. It passes the BIOS menu, cites it is booting from hd0,0 then goes through the white Ubuntu logo screen fine. After that, it stops at a navy blue screen, where nothing is there and even if I leave it on for around thirty mins nothing happens. I have to manually hold down the power button until it turns off and repeat about five times. I believe this is due to the new GRUB 2. GRUB "Legacy" (9.04 version) works fine with my PC and booting is not a problem. Here is my PC stats from System Monitor:

Ubuntu
Release 9.04 (jaunty)
Kernel Linux 2.6.28-16-generic
GNOME 2.26.1


Hardware
Memory: 748.2 MB
Processor: Intel Pentium 4 CPU 2.00 GHz

System Status
Available Disk Space: 63.1 GB


Any incompatibilties with GRUB 2 here?

---

### Post by dcstar on 2009-11-23
> **aust77 said:**
> I have bounced between 9.04 and 9.10 over the past two weeks, due to booting problems.
.........

If Grub2 is not working properly simply install the legacy Grub. There are instructions searchable on the web.

---

### Post by jmszr on 2009-11-23
aust77,

Here is a Grub 2 introduction: [http://ubuntuforums.org/showthread.php?t=1285897](http://ubuntuforums.org/showthread.php?t=1285897) . Perhaps something in there will be of help.

And if you decide to revert to Legacy Grub: [http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932) .

---

### Post by aust77 on 2009-11-24
Thank you both jmszr and dcstar. It seems to be working fine, and if I run into any problems I will simply revert to GRUB-Legacy.


Thanks,


aust77

---

