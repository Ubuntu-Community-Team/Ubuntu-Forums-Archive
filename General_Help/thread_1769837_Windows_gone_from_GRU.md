---
title: "Windows gone from GRU"
date: 2011-05-28
forum: General Help
---

### Post by u_p_s on 2011-05-28
Hi there,

I have Lubuntu and Windows has disappeared from the GRUB. I have seen in other questions that it is usually solved editing menu.lst, but I don have such a file in /boot/grub/

How I can fix  it, please?

Thanks.


This is the output of 
$ fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa5faa5fa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2709    20480008+   7  HPFS/NTFS
/dev/sda2            2710       10336    57660089+   f  W95 Ext'd (LBA)
/dev/sda5            2710        4056    10183288+  83  Linux
/dev/sda6            4057        4199     1081048+  82  Linux swap / Solaris
/dev/sda7            4200       10336    46395688+   7  HPFS/NTFS

Disk /dev/sdb: 20.0 GB, 20020396032 bytes
240 heads, 63 sectors/track, 2586 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3a7043c3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2        2586    19542600    f  W95 Ext'd (LBA)
/dev/sdb5               2        2586    19542568+   7  HPFS/NTFS

---

### Post by prodigy_ on 2011-05-28
The most basic method is to run ```
sudo update-grub
``` command and see if Windows will reappear.

If this won't help, can you run boot info script (see the link in my sig) and post the results file to provide more info? Speaking of **menu.lst** - you don't have it because grub2 stores its config in **/boot/grub/grub.cfg**.

---

### Post by Quackers on 2011-05-28
Has Windows ever appeared in your grub menu? If so what happened to make it disappear?

---

### Post by SteveDee on 2011-05-28
> **u_p_s said:**
> Hi there,

I have Lubuntu and Windows has disappeared from the GRUB....

You may need to install os-prober: [http://ubuntuforums.org/showthread.php?t=1658838](http://ubuntuforums.org/showthread.php?t=1658838)

---

