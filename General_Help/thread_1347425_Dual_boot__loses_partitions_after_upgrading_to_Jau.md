---
title: "Dual boot  loses partitions after upgrading to Jaunty"
date: 2009-12-06
forum: General Help
---

### Post by opossum2007 on 2009-12-06
Hi,

Apologies for posting here what may be a Windows problem.  Windows is not recognising partitions after I upgraded my dual boot system from 8.04LTS to Jaunty.

I did not upgrade directly from Hardy, but installed from the Live CD and overwrote sda7.  I would have tried Karmic, but the Live CD does not display and gives an "out of range" error on my monitor.

My system is organised as follows:

IDE disk 1
sda1 windows 7RC (primary partition)
extended partition
sda5 swap
sda6 ntfs (labelled Files)
sda7 Ubuntu root
sda8 /home

IDE disk 2
sdb1 ntfs (labelled A) (primary partition)
sdb2 ntfs (labelled B) on extended partition.

When using Hardy, I could boot into either operating system and everything was recognised by Windows and Ubuntu, but now after upgrading, Windows does not recognise partitions A or B (they are visible to the disk manager).

My first attempt to boot Windows after the upgrade failed because it was looking at the wrong partion.

Grub's menu.lst entry for windows was as follows:

rootnoverify (hd1,0)
??????????? (not sure what this line contained)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1.

I changed root to hd(0,0) and removed the map lines.  Windows now boots, but drives A and B are not visible.

Jaunty is working fine, and I don't believe I'll use Windows7 once the RC runs out.

Any help would be appreciated.

Thanks,
Mel

---

### Post by opossum2007 on 2009-12-06
Mea Culpa.

It was Windows fault.  Just needed to get the Disk Manager to assign letters, since it did not do it automatically.

---

