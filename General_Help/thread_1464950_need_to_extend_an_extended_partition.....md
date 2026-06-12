---
title: "need to extend an extended partition...."
date: 2010-04-28
forum: General Help
---

### Post by myjess on 2010-04-28
Hi,
I need to extend the start of an extended partition by approx 20gb into the unallocated space before it. This partition holds this modified ubuntu netbook karmic install that is running now. I need to do this with ubuntu running. 

Any ideas?

Thanks.

---

### Post by inputpower on 2010-04-28
Gparted works great. Make sure you backup first.

---

### Post by srs5694 on 2010-04-28
GParted won't operate on a partition that's currently in use, so if your installation uses any logical partitions, GParted won't do the job when you're currently running the installation from the hard disk. If your only in-use logical partition is swap space or something else non-critical, you could stop using it to do the operation.

In theory, you can do it with sfdisk:


[list=1]
[*]Back up your system. If you can't do this, think long and hard before proceeding, since a mistake will render your system unbootable; you'll need an emergency recovery disc, which I get the impression is a problem for you.
[*]Type "sudo sfdisk -d /dev/sda > parts.txt" to create a plain-text file with your partition definitions. (Change /dev/sda as necessary and use any filename you like for the backup file; there's nothing special about parts.txt.)
[*]Back up parts.txt so you can revert to the original layout if you have problems.
[*]Load parts.txt into a text editor.
[*]Locate the extended partition definition and modify the start point appropriately. You'll need to do the math to put the start point after the end point of the preceding primary partition, since each partition is defined as a start point and size. (Normally there'll be no gap.)
[*]Save your changes.
[*]Type "sudo sfdisk /dev/sda < parts.txt" to write the changed layout to disk. Sometimes you must add a "-f" between "sfdisk" and "/dev/sda"; but don't do this until you've read and understood any error message and are sure that you really want to ignore it. Also, change /dev/sda and parts.txt to whatever is appropriate for your system, as above.
[*]Reboot and hope everything works. If it doesn't, you'll have a very hard time recovering.
[/list]


If your netbook is a Linux-only netbook, it might actually be safer to convert from the Master Boot Record (MBR) partitioning scheme to the GUID Partition Table (GPT) system, using my [GPT fdisk](http://www.rodsbooks.com/gdisk/) or some other tool. GPT does away with the primary/logical/extended partition distinction, so there's then no need to resize extended partitions. Windows, however, can't boot from GPT disks on BIOS-based computers. Also, if you make this change, you'll have to re-install your boot loader. If you forget to do this, your system will be rendered unbootable.

Overall, it's risky whatever you do. Perhaps you could post the output of "sudo fdisk -l" or a screen shot of GParted showing your disk and describe your goal. There may be an easier or safer way to do it.

---

### Post by myjess on 2010-04-29
here's a parted list.

(parted) print free
Model: ATA ST9120817AS (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  46.5GB  46.5GB  primary   ntfs
        46.5GB  64.0GB  17.4GB            Free Space
 4      64.0GB  97.5GB  33.5GB  extended
 5      64.0GB  96.1GB  32.1GB  logical   ext4
 6      96.1GB  97.5GB  1423MB  logical   linux-swap(v1)
 2      97.5GB  97.7GB  210MB   primary   ext4            boot
 3      97.7GB  120GB   22.3GB  primary                   lvm


parts 2 & 3 are fedora12 which i wish to keep

part 2 is not the boot anymore, as I installed ubuntu after fedora12, and the ubuntu part (5) nows seems to be the boot for all, especially after i modified grub2 in ubuntu.

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x05a405a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5657    45439821    7  HPFS/NTFS
/dev/sda2   *       11853       11878      204800   83  Linux
/dev/sda3           11878       14593    21812282+  8e  Linux LVM
/dev/sda4            7779       11852    32724405    5  Extended
/dev/sda5            7779       11679    31334751   83  Linux
/dev/sda6           11680       11852     1389591   82  Linux swap / Solaris

Partition table entries are not in disk order

thanks.

---

### Post by srs5694 on 2010-04-29
You still haven't described your goal: What do you intend to do with that free space? Do you want to use it in Linux or Windows, and for what purpose? Also, can you afford to discard any of your primary partitions, and are you currently using your NTFS partition to boot Windows? Finally, do you have any way to boot any type of medium other than your hard disk? If so, it may be safest to use that tool to boot a Linux emergency disc with GParted or something similar to add or modify partitions.

Basically, you're out of primary partitions, which means you must expand your extended partitions (as you first suggested), resize or recreate /dev/sda1, or convert to GPT.

---

### Post by psusi on 2010-04-29
Why do you have such a messed up partition layout?  Two non lvm partitions plus an lvm?  If you are using lvm then you want the whole disk to be one single lvm partition to use as the lvm physical volume, then have lvm carve that up into logical volumes however you like.  Then you can move them around or make them larger all you like even while they are in use.

At any rate, yes, you can not modify partitions that are in use so you will have to boot from a live cd and run gparted from there.

---

