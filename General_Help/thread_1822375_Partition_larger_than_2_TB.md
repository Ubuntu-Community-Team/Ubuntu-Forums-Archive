---
title: "Partition larger than 2 TB?"
date: 2011-08-10
forum: General Help
---

### Post by Excizted on 2011-08-10
Hello,

On a Ubuntu 11.04 x64 Server with a 6 TB raid array I am experiencing something strange.

Once i enter fdisk using

```
fdisk /dev/sdb
```and create a partition, then the maximum number of blocks I can have, equals to 2 TB of disk space.

Does this mean, that I can't create a partition larger than 2 TB?

I also tried creating another partition, however the maximum number of blocks on the second partition equaled to 1,5 TB.
Creating a third partition was weird - although choosing the last block of the second partition as the starting block, and the maximum block as ending block, the partition showed, when fdisk was issued **p**, that the block range was within the other partitions?!

Am I doing something wrong trying to partition the disk, or should I split the raid array into 3x 2 TB raid arrays instead?


Generally I don't see the point why a partition should be limited to such small an amount as 2 TB?

Hope someone has a clue.

Thanks.

---

### Post by WorMzy on 2011-08-10
What partition table are you using on the disk/array? MBR is limited to 2TiB partitions. GPT, however, has no such limit, as far as I am aware.

---

### Post by Excizted on 2011-08-10
> **WorMzy said:**
> What partition table are you using on the disk/array? MBR is limited to 2TiB partitions. GPT, however, has no such limit, as far as I am aware.

How do I see what partition table I am using, and eventually change it?

---

### Post by WorMzy on 2011-08-10
```
sudo parted -l
```

e.g.

```
wormzy@sakura[pts/1]:~$ sudo parted -l
Model: ATA SAMSUNG HD103SJ (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: **_gpt_**

Number  Start   End     Size   File system  Name  Flags
 1      1049kB  700GB   700GB  xfs
 2      700GB   1000GB  300GB  xfs


Model: ATA SAMSUNG HD103UJ (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: **_msdos_**

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  1000GB  1000GB  primary  ntfs         boot
```

msdos = MBR

You can use parted to create new partition tables. This will show you how:
[http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html](http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html)

---

### Post by oldfred on 2011-08-10
You can also use gdisk.

GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)


I do not know enough about RAID to know if you need a bios_grub partition but would suspect you do.

Since the BIOS Boot Partition ("bios_grub" flag set in GNU Parted) is used without a filesystem for storing GRUB 2 boot code "unknown" filesystem! may be shown in many Partition tools.

However, in the GPT setup, there is no space following the 512-byte MBR for embedding the "second stage" core.img. Thus, you must make a separate "BIOS boot partition" to hold core.img. You can set bios_grub flag in gparted or with command line: In GPT fdisk (gdisk), give it a type code of EF02.
BIOS Boot Partition of 1 MiB for partition alignment.

---

### Post by Excizted on 2011-08-10
> **WorMzy said:**
> ```
sudo parted -l
```e.g.

```
wormzy@sakura[pts/1]:~$ sudo parted -l
Model: ATA SAMSUNG HD103SJ (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: **_gpt_**

Number  Start   End     Size   File system  Name  Flags
 1      1049kB  700GB   700GB  xfs
 2      700GB   1000GB  300GB  xfs


Model: ATA SAMSUNG HD103UJ (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: **_msdos_**

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  1000GB  1000GB  primary  ntfs         boot
```msdos = MBR

You can use parted to create new partition tables. This will show you how:
[http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html](http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html)

Is this guide correct, that  I have to recompile the Linux kernel?

---

### Post by WorMzy on 2011-08-10
Not sure about that. It's a four year old tutorial, so it may be out of date.

Run
```
zgrep EFI_PARTITION /proc/config.gz
```
and if it says
```
CONFIG_EFI_PARTITION=y
```
Then you don't need to recompile the kernel.

(I'm assuming the Ubuntu kernel has /proc/config.gz enabled)

---

### Post by oldfred on 2011-08-10
I have never compiled a kernel and have been using gpt with Maverick (BIOS system) since it was in beta.

Some have posted about using UEFI to boot, while a few have it working there are some issues with grub2.

---

### Post by srs5694 on 2011-08-10
The standard Linux fdisk utility works only on MBR disks and on some more exotic disk types, but not on GPT disks. Thus, from post #1 it's obvious that you're trying to create MBR partitions, not GPT partitions. To create or modify GPT partitions, you must use gdisk (an fdisk workalike) or a libparted-based tool (parted, GParted, etc.), as others have said.

Since your initial example shows you working on /dev/sdb, it appears that you've got a true hardware RAID controller. With such a controller, you can treat the array as if it were a physical disk of that size, so you don't need to worry about some of the software RAID issues that can cause problems sometimes. If you're booting in BIOS mode, though, you'll need to create a ~1 MiB [BIOS Boot Partition,](http://en.wikipedia.org/wiki/BIOS_Boot_partition) as oldfred has said; and you'll need to ensure that your kernel falls below the 2 TiB mark. The most reliable way to do this is to create a separate /boot partition (which is entirely different from the BIOS Boot Partition) and put the /boot partition before the 2 TiB mark on the disk. If you've got a new motherboard with UEFI support, you should create a ~200-250MB [EFI System Partition (ESP)](http://en.wikipedia.org/wiki/EFI_System_partition) instead of a BIOS Boot Partition. If you're not sure which you've got, you can create both partitions.

You do *not* need to recompile an Ubuntu kernel to use GPT -- at least, not any recent version of Ubuntu. I've got several 11.04 installations on GPT disks with stock kernels and they're all fine.

---

### Post by Excizted on 2011-08-11
> **srs5694 said:**
> The standard Linux fdisk utility works only on MBR disks and on some more exotic disk types, but not on GPT disks. Thus, from post #1 it's obvious that you're trying to create MBR partitions, not GPT partitions. To create or modify GPT partitions, you must use gdisk (an fdisk workalike) or a libparted-based tool (parted, GParted, etc.), as others have said.

Since your initial example shows you working on /dev/sdb, it appears that you've got a true hardware RAID controller. With such a controller, you can treat the array as if it were a physical disk of that size, so you don't need to worry about some of the software RAID issues that can cause problems sometimes. If you're booting in BIOS mode, though, you'll need to create a ~1 MiB [BIOS Boot Partition,]("http://en.wikipedia.org/wiki/BIOS_Boot_partition") as oldfred has said; and you'll need to ensure that your kernel falls below the 2 TiB mark. The most reliable way to do this is to create a separate /boot partition (which is entirely different from the BIOS Boot Partition) and put the /boot partition before the 2 TiB mark on the disk. If you've got a new motherboard with UEFI support, you should create a ~200-250MB [EFI System Partition (ESP)]("http://en.wikipedia.org/wiki/EFI_System_partition") instead of a BIOS Boot Partition. If you're not sure which you've got, you can create both partitions.

You do *not* need to recompile an Ubuntu kernel to use GPT -- at least, not any recent version of Ubuntu. I've got several 11.04 installations on GPT disks with stock kernels and they're all fine.

Thank you, I'll try fooling around with GPT.
Yes, it is a hardware raid controller in the server.

I am getting kinda confused with the BIOS/EFI partition?
As you might notice from /dev/sdb, I do have a partitioned and functioning /dev/sda which the system and kernel runs on. The 6 TB raid array (/dev/sdb) is for storage only, so do I need those at all?

Thanks!

---

### Post by Excizted on 2011-08-11
I have now partitioned the disk with **gdisk** (which I simply had to install from *apt-get*) and it was completely like using **fdisk**.

**mkfs** and **tune2fs** commands worked fine, and I have now mounted the disk which in **df** is shown to be of 6 TB in size.

So I should be all good, right?

---

### Post by srs5694 on 2011-08-11
> **Excizted said:**
> I am getting kinda confused with the BIOS/EFI partition?
As you might notice from /dev/sdb, I do have a partitioned and functioning /dev/sda which the system and kernel runs on. The 6 TB raid array (/dev/sdb) is for storage only, so do I need those at all?

If the system's already booting from another disk, you needn't be concerned with them.

> **mkfs** and **tune2fs** commands worked fine, and I have now mounted the disk which in **df** is shown to be of 6 TB in size.

So I should be all good, right?

It sounds like it! Try writing some files to the disk and then reading them back to be sure it's working correctly. If it is, you can mark this thread as solved.

---

