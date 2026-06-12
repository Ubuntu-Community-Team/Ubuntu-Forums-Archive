---
title: "Toshiba Satellite A135-S4656 Video Driver"
date: 2009-10-14
forum: General Help
---

### Post by Neckbeard Stallman on 2009-10-14
Hi I am new to GNU/Linux and I have installed Ubuntu on a Toshiba Satellite A135-S4656 and need help installing the correct Video Driver. Here is my lspci | grep VGA

user@user:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

sudo lshw -C Video 

*-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0


any help?

---

### Post by Neckbeard Stallman on 2009-10-15
Bump

---

