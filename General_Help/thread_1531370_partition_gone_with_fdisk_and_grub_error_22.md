---
title: "partition gone with fdisk and grub error 22"
date: 2010-07-14
forum: General Help
---

### Post by cli168 on 2010-07-14
need lots of help.

setup:  dual boot windows xp and ubuntu 8.1

I was installing software and ran out of space on the ubuntu side.  Use gparted to shrink the xp partition and add to ubuntu.  Booted back to ubuntu and see lots of error with fdisk.  I use fdisk to try to fix it (x, f, v), but still got error.  I then install testdisk and try to use it to fix the error.  After I ran thru testdisk and reboot, I now got grub error 22.  I use the liveCD and boot back in.  When I use fdisk, I only see 1 partition, /dev/sda1 FAT16 with 40M.  I use qparted and also see only one partition, the other space is unpartitioned.  When I go back to issue sudo fdisk /dev/sda1, I see this:

Command (m for help): p

Disk /dev/sda1: 41 MB, 41094144 bytes
255 heads, 63 sectors/track, 4 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x481ec400

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/sda1p1   ?           1           1           0   42  SFS
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(288, 73, 15) logical=(0, 0, 1)
Partition 1 has different physical/logical endings:
     phys=(256, 73, 14) logical=(267349, 89, 4)
Partition 1 does not end on cylinder boundary.
/dev/sda1p2   ?       33858      150245   934885682+   0  Empty
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(256, 6, 10) logical=(33857, 1, 42)
Partition 2 has different physical/logical endings:
     phys=(836, 16, 3) logical=(150244, 227, 13)
Partition 2 does not end on cylinder boundary.
/dev/sda1p3   ?         294        7038    54165760   ff  BBT
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(614, 114, 33) logical=(293, 209, 46)
Partition 3 has different physical/logical endings:
     phys=(0, 6, 62) logical=(7037, 37, 41)
Partition 3 does not end on cylinder boundary.
/dev/sda1p4   ?         467       80148   640033442   20  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(367, 0, 14) logical=(466, 170, 61)
Partition 4 has different physical/logical endings:
     phys=(353, 108, 47) logical=(80147, 37, 58)
Partition 4 does not end on cylinder boundary.

Question: will I be able to recover from this?

Please help.  

Thanks.

---

### Post by vijuec on 2010-08-13
.

---

