---
title: "Partition issues on 10.04 LTS - Partitions not ending on cylinder boundries?"
date: 2011-01-16
forum: General Help
---

### Post by lpetro on 2011-01-16
Hi Everyone,

I have installed 10.04 LTS on a few computers lately (stuck at home due to recent surgery and am trying to kill some time) and have been running into some odd issues and cannot figure out what is going on.  I am hoping someone can help me out here.

The installation appears to work fine every time.  The systems also appear to be running without any issues.  The weird thing is that every time I run an fdisk -l command, I always get these types of messages:

Disk /dev/sda: 3221 MB, 3221225472 bytes
255 heads, 63 sectors/track, 391 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005437b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13       96256   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              13         392     3047424   8e  Linux LVM
Partition 2 does not end on cylinder boundary.

cfdisk also gives similar errors:

 FATAL ERROR: Bad primary partition 1: Partition ends in the final partial cylinder

I am not doing anything out of the ordinary when installing Ubuntu (as far as i can tell that is).  I am not pre-partitioning with external tools for example.  I use the Ubuntu installer to setup my partitions.

Does anyone have any insight they can offer?

Thanks,
lpetro

---

### Post by srs5694 on 2011-01-16
The cylinder boundary warnings should not concern you; this is just a reflection of the fact that fdisk is warning about non-compliance with a long-ago standard (namely, starting and ending partitions on fictitious cylinder boundaries) that's now been abandoned. The libparted-based tools in Ubuntu's installer apparently followed the newer standard of starting partitions on 1 MiB boundaries.

The "FATAL ERROR" is probably a reflection of the same thing, but to be 100% sure there's no problem, type "sudo fdisk -lu /dev/sda" (note the "u" in "-lu") to see the partition start and end points in sectors, rather than the imprecise cylinder values that fdisk uses by default. Check that no partition extends beyond the end of the disk (when launched with "-lu", fdisk will report the exact size of the disk in sectors). If not, you're fine.

You could check to see if there's an upgrade to the util-linux package in Ubuntu 10.04. If so, install it; that might give you an fdisk that's a little less Chicken Little about these issues, but I can make no promises on that score, since I'm not sure precisely what fdisk complains about or when. I think you're less likely to see complaints if you use the "-u" and/or "-c" options, though.

If these are Linux-only computers, you might also consider using the [GUID Partition Table (GPT)](http://en.wikipedia.org/wiki/GUID_Partition_Table) rather than the older [Master Boot Record (MBR)](http://en.wikipedia.org/wiki/Master_boot_record) for partitioning. GPT uses sector values, and cylinder values are meaningless to it, so this won't be much of an issue. OTOH, that's partly because fdisk doesn't work with GPT disks; instead, you'd use GNU Parted or [GPT fdisk (gdisk),](http://www.rodsbooks.com/gdisk/) gdisk being an fdisk workalike that I wrote for GPT disks. If you go this route, be sure to create a small (35 KiB to 1 MiB) [BIOS Boot Partition](http://grub.enbug.org/BIOS_Boot_Partition) when you install Linux; GRUB will be happier that way. GPT offers some minor and one major advantage over MBR, the major advantage being that it uses 64-bit sector pointers, which means you can use much bigger disks with GPT. The minor advantages include elimination of the primary/extended/logical partition distinction, duplication of partition data at the start and the end of the disk for safety, stored CRCs of partition data to detect errors, and partition labels to help you identify partitions' purposes.

---

### Post by lpetro on 2011-01-16
Thanks for the reply srs5694... here is the output of fdisk -lu:


netbook% sudo fdisk -lu /dev/sda
[sudo] password for ****:

Disk /dev/sda: 3221 MB, 3221225472 bytes
255 heads, 63 sectors/track, 391 cylinders, total 6291456 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005437b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      194559       96256   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2          194560     6289407     3047424   8e  Linux LVM
Partition 2 does not end on cylinder boundary.
netbook%


I also ran a parted -l and got the following:


netbook% sudo parted -l
Model: VMware, VMware Virtual S (scsi)
Disk /dev/sda: 3221MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  99.6MB  98.6MB  primary  ext2         boot
 2      99.6MB  3220MB  3121MB  primary               lvm


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/system-swap: 604MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system     Flags
 1      0.00B  604MB  604MB  linux-swap(v1)


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/system-home: 516MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  516MB  516MB  ext3


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/system-var: 998MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  998MB  998MB  ext3


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/system-root: 998MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  998MB  998MB  ext3


netbook% man parted
netbook% sudo fdisk -lu /dev/sda
[sudo] password for lpetro:

Disk /dev/sda: 3221 MB, 3221225472 bytes
255 heads, 63 sectors/track, 391 cylinders, total 6291456 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005437b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      194559       96256   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2          194560     6289407     3047424   8e  Linux LVM
Partition 2 does not end on cylinder boundary.
netbook% sudo parted -l
Model: VMware, VMware Virtual S (scsi)
Disk /dev/sda: 3221MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  99.6MB  98.6MB  primary  ext2         boot
 2      99.6MB  3220MB  3121MB  primary               lvm


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/system-swap: 604MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system     Flags
 1      0.00B  604MB  604MB  linux-swap(v1)


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/system-home: 516MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  516MB  516MB  ext3


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/system-var: 998MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  998MB  998MB  ext3


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/system-root: 998MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  998MB  998MB  ext3


netbook%

---

### Post by srs5694 on 2011-01-16
> **lpetro said:**
> Thanks for the reply srs5694... here is the output of fdisk -lu:


netbook% sudo fdisk -lu /dev/sda
[sudo] password for ****:

Disk /dev/sda: 3221 MB, 3221225472 bytes
255 heads, 63 sectors/track, 391 cylinders, total [COLOR=Red]6291456[/COLOR] sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005437b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      194559       96256   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2          194560 [COLOR=Red]    6289407[/COLOR]     3047424   8e  Linux LVM
Partition 2 does not end on cylinder boundary.
netbook%

6291456 > 6289407, so you're fine.

---

