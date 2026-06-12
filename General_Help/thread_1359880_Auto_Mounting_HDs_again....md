---
title: "Auto Mounting HDs again..."
date: 2009-12-20
forum: General Help
---

### Post by NEUR0M4NCER on 2009-12-20
So I managed to squeeze another HD into the box, as a desperate solution for a bit more space. Problem is, it's IDE, as opposed to the three Sata drives that were there already, and it appears to have mucked up the mount points.

Here's the output of sudo fdisk -l:
```

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6c136ec4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       14945   120045681    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14105   113298381   83  Linux
/dev/sdb2           14106       18707    36965565    7  HPFS/NTFS
/dev/sdb3           18708       19457     6024343+  82  Linux swap / Solaris

Disk /dev/sdd: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00073bed

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      182401  1465136001   83  Linux

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004b15b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      182401  1465136001   83  Linux

```

and here's my /etc/fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=6ae8b74e-97ed-4b15-8031-2a7cdc8ea004 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=f0115bc3-7656-47c9-84c5-6f417231fa7d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   auto user,noauto,exec,utf8 0       0
/dev/sdc1       /storage-0      ext3    defaults        0       0
/dev/sdb1       /storage-1      ext3    defaults        0       0

```

What do I need to do to get them all auto-mounted again? And am I right in saying that it's changed the mount point of my boot-flagged disk (should I even still be able to boot into it??)?

---

### Post by oldfred on 2009-12-20
Mixed drives seem to cause lots of issues, both with old grub and it seems more so with new grub2.

Often the ide drive becomes the first drive in the drive chain. Then you need to have grub installed to it to be able to boot. The boot flag is only used by windows ( and maybe some other operating systems) but not by Ubuntu. The windows boot loader looks for the boot flag to boot. 

You need to check your BIOS and see if you can reorder drives. My current system is all Sata and the sda, sdb, sdc is the order they are plugged into the sata ports. When in Bios I changed to boot from sdc it did not change any drive order.  You may want to check your /boot/grub/device.map to see what it has.

This reinstalls grub and lets you set which drive to boot from:
reinstalls grub and allows choice of which drive to install to. Choose boot drive if not sda
sudo dpkg-reconfigure grub-pc

---

