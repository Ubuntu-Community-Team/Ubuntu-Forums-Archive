---
title: "new project"
date: 2011-06-04
forum: General Help
---

### Post by wlm2 on 2011-06-04
I try to install openbsd with ubuntu live cd on alix6e1 board ( cf card 4gb).
After all the installation process and install sets by default.
I am rebooting the board and remove the possibility of pxeboot from the bios Options.
Board recognizes the cf card and tries to boot from hd0 while in the installation process he just recognize 
only wd0 and install everything in wd0.
In any case when the board is after the installation process, is not detecting the installation drive.
01F0 Master 044A CF CARD 4GB 
Phys C/H/S 1966/16/63 Log C/H/S 983/32/63 
Using drive 0, partition 3; 
Loading;... 
probing: pc0 com0 pci mem[640K 255M a20=on] 
disk: hd0 
>> OpenBSD/i386 BOOT 3.01 
boot> 
booting hd0a:/bsd: 5665588+872060 [52+291168+272312]=0x6c5c70 
entry point at 0x200120 
 
Can someone give me a hint

---

