---
title: "Partition restore with TestDisk and RAID 5"
date: 2009-12-23
forum: General Help
---

### Post by rdunnion on 2009-12-23
I have been trying to install Mac OS X on my PC, after a bunch of fussing with my BIOS I got the install disk to run (yay!!) but it wouldn't read the partition I had allocated for it (boooo!). So I (ahem) had Ubuntu and Windows partitions and was attempting to format the Mac partition with HFS+ so that the install disk would see it. Well as the saying goes "inexperience makes strange bedfellows" (or something like that) I blew out all my partitions with gparted accidentally. So now I'm trying to restore all partitions with TestDisk and Ubuntu liveCD. The only problem is TestDisk is seeing my RAID array as individual disks. How can I get it to see the hardware RAID array? Thanks :) - Ryan

---

### Post by rdunnion on 2009-12-23
Wait a minute I may have found it. Would this be my RAID array:
Disk /dev/mapper/nvidia_babecfcf
I have a NVIDIA chipset.

---

