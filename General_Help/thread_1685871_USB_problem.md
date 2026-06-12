---
title: "USB problem"
date: 2011-02-11
forum: General Help
---

### Post by Benbow on 2011-02-11
I have just attempted to format my 16gb usb stick with EXT 3 but for some reason it came up with an error and now it cannot see the stick at all.
I used gparted. Can I rescue my 16gb usb?
I have just added this - I am pretty sure that I failed to unmount the usb after getting the problem. Can it still be rescued?

---

### Post by RedSingularity on 2011-02-11
With the usb drive plugged in, post the output of "sudo fdisk -l"

---

### Post by Benbow on 2011-02-11
Thanks, here it is (I don't know if this is relevant but I have a 1tb drive with  win 7 on 500gb)

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
60 heads, 12 sectors/track, 2713229 cylinders
Units = cylinders of 720 * 512 = 368640 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2e5fafb1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1     1405387   505939157    7  HPFS/NTFS
/dev/sda2         1405389     2713228   470821889    5  Extended
/dev/sda5         1405389     2663359   452869120   83  Linux
/dev/sda6         2663362     2713228    17951744   82  Linux swap / Solaris

Disk /dev/sdc: 16.0 GB, 16039018496 bytes
64 heads, 32 sectors/track, 15296 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ad86d

   Device Boot      Start         End      Blocks   Id  System
benbow@benbow-System-Product-Name:~$

---

### Post by RedSingularity on 2011-02-11
Yeah, use gparted to format it again.  Make sure the "boot" flag is not on.

---

