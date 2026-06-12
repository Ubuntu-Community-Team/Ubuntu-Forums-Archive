---
title: "Problem booting 12.04 from ssd"
date: 2012-04-19
forum: General Help
---

### Post by soyuz_one on 2012-04-19
Hi

A few days ago I put 12.04(beta2) on a ocz vertex 3 (ssd) as a single boot system on a Thinkpad 420. Previously I've dealt with dual-booting ubuntu and windows but this is my first time with a single OS. It's also my first time installing an OS on an ssd. The OS seems to be working fine but it does not boot automatically. Normally I would expect to see a grub screen as for a dual-boot system but I do not see any. The following is my loading scenario:

After the splashscreen pops up I get the prompt

 "Intel(R) Boot Agent GE v1.3.xx. Copyright (c) 1997-2007, Intel corporation.
Intel(R) Boot Agent PXE Base Code (PXE-2.1 build 086)
Copyright © 1997-2007, Intel Corporation&#8221;
and "Initializing and establishing link ...".

Then after a few seconds: "PXE-E61: Media test failure." and "PXE-M0F: Exiting Intel Boot Agent." 

Then I get the option of booting (in a bios type screen):
- ubuntu
- ocz vertex 3 ....
- from network
- from CD/DVD

Then hitting either ESC or Enter gets ubuntu up and running.  

I tried googling for a solution but I haven't found anyone with the same problem. I got it into my head that it was a problem with the bootloader and one of the things I tried was the advice from this page
[http://mygeekopinions.blogspot.com/2011/06/install-boot-repair-in-ubuntu-1104.html]("http://mygeekopinions.blogspot.com/2011/06/install-boot-repair-in-ubuntu-1104.html") but it did not have an effect.


I could try reinstalling the system again but I've stupidly put time into installing applications and such, so hopefully that could be avoided. At the very least I'd like to have a rough idea of what the problem is so that I could make an informed decision as to what I should do next.

In case it helps I'll give my fdisk output

ThinkPad-T420:~$ sudo fdisk -l 

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   234441647   117220823+  ee  GPT

---

### Post by oldfred on 2012-04-19
fdisk does not show partitions on gpt disks. Are you booting with UEFI or BIOS?

Post this:

sudo parted /dev/sda unit s print

If BIOS, you need a bios_grub partition. But it looks more like you are booting with UEFI and it is trying to network boot first?

---

### Post by soyuz_one on 2012-04-20
ThinkPad-T420:~$ sudo parted /dev/sda unit s print

Model: ATA OCZ-VERTEX3 (scsi)
Disk /dev/sda: 234441648s
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start       End         Size        File system     Name  Flags
 1      34s         195346s     195313s     fat32                 bios_grub
 2      195347s     217896518s  217701172s  ext4
 3      217896519s  234441598s  16545080s   linux-swap(v1)


When I installed 12.04 I did not make any custom changes so I would assume that it would boot with UEFI. As soon as ubuntu was installed I had this boot problem but I may have confused bios with UEFI since then.

---

### Post by oldfred on 2012-04-20
If you have UEFI, then you need the first partition to be the efi partition. If booting with BIOS you need a 1MB unformated bios_grub partition. Your bios_grub is formated to FAT.

An EFI System Partition EF00 (~100 to -256MiB, FAT32) for UEFI, a BIOS Boot Partition EF02 (~1MiB, no filesystem) for BIOS, and whatever partitions you want for Linux. 

You must set the partition type codes correctly, but how you do this depends on the utility you use to create them. Also, you should be sure to create a GUID Partition Table (GPT) on the disk, not a Master Boot Record (MBR) partition table. In BIOS mode, Ubuntu's installer defaults to creating MBR partitions, at least on sub-1TB disks, so you may need to use another utility to do the partitioning. You do not need both but it does not hurt as both are small, and then you can configure easily to boot with either UEFI or BIOS. You can boot via bios AND efi (after setting up your efi boot entry using efibootmgr or via efi shell and running the efi binary)

Did you use old partiitoning tools to format drive. Sectors need to be divisible by 8.

[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)
[https://wiki.archlinux.org/index.php/Grub2](https://wiki.archlinux.org/index.php/Grub2)

GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)
srs5694's to show 8 sector alignment post #9
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)

If you are booting only one system, grub does not present a menu as you do not normally need it. You should be able to hold shift key from BIOS till menu appears if you want the menu.

I did not put discard in my fstab right away and ran this:

Alternate to discard, call fstrim via cron
[http://opensuse.14.n6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html](http://opensuse.14.n6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html)

fred@fred-Precise:~$ cat /sys/block/sda/queue/scheduler
noop deadline [cfq] 
fred@fred-Precise:~$ sudo fstrim -v /
/: 23267893248 bytes were trimmed

---

### Post by soyuz_one on 2012-04-20
Using gparted I get

sudo gdisk /dev/sda
GPT fdisk (gdisk) version 0.8.1

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.

Command (? for help): p
Disk /dev/sda: 234441648 sectors, 111.8 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): blah-blah-blah
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 234441614
Partitions will be aligned on 1-sector boundaries
Total free space is 16 sectors (8.0 KiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              34          195346   95.4 MiB    EF02  
   2          195347       217896518   103.8 GiB   0700  
   3       217896519       234441598   7.9 GiB     8200  


Does this mean that I still have to convert the MBR to GPT and if so [https://wiki.archlinux.org/index.php/GPT#GUID_Partition_Table]("https://wiki.archlinux.org/index.php/GPT#GUID_Partition_Table") tells to to 

"Just open the MBR disk using gdisk:"

How is this done?

Note my understanding at this stage is that I need to convert MBR to GPT and then create a new EF00 with 256MB and my system should work. Is this correct?

---

### Post by oldfred on 2012-04-20
I think you just need to change sda1 from ef02 to ef00 to be the efi partition. It is a 100MB so that is ok if only booting one system. But you may want to repartition to make sure starts are divisible by 8.

---

### Post by soyuz_one on 2012-04-20
My sectors now look like this

Number  Start (sector)    End (sector)  Size       Code  Name
   1              34          195346   95.4 MiB    EF00  
   2          195347       217481215   103.6 GiB   0700  
   3       217896519       234441598   7.9 GiB     8200  


I'm still getting the same boot behavior though. Do I need to change something in the EF00 partition?

I was unable to move the start points with gdisk. I tried using the 'l' option in the expert section (set the alignment value) but it seem to have only a passive effect (it just gives me warnings that the partitions are not aligned properly).  

I also tried partitionmanager but this does not allow for control over the startpoints.

---

### Post by soyuz_one on 2012-04-20
This may be useful

Here is the output from gdisk's 'set attribute' command

Expert command (? for help): a
Partition number (1-3): 1
Known attributes are:
0: system partition
1: hide from EFI
2: legacy BIOS bootable
60: read-only
62: hidden
63: do not automount

I assume this partition should not be hidden from the EFI and also that it should not be legacy bios bootable. I'd like to get some verification that I am on the right track here!

Thanks for your assistance oldfred!!

---

### Post by oldfred on 2012-04-20
You should just need to set the code to ef00 with - t in gdisk or in gparted just set the boot flag.

> Change a partition's GUID type code to the one specified by *hexcode*. Note that *hexcode* is a gdisk/sgdisk internal two-byte hexadecimal code. You can obtain a list of codes with the -L option.

---

### Post by soyuz_one on 2012-04-20
You may have missed a previous message. The first partition has already been set to EF00 and has the boot flag. Still no change though, unfortunately.

---

### Post by oldfred on 2012-04-20
Where are you at install wise. You would have to at least reinstall grub to get it to see the UEFI. And most have posted that only works if flash drive is booted in UEFI mode.

grub EFI -skodabenz
1. Most of the modern UEFI systems come with GPT instead of MBR.
2. GRUB needs to be installed to the ESP (EFI SYSTEM PARTITION). The ESP has to be the first partition in the drive, with file system of a FAT variant, and it has to be larger then 100 MiB (200MiB or more recommended). Ubuntu mounts the ESP by default in /boot/efi .
3. After you install grub in the ESP, you need to make a boot entry for it using efibootmgr, or you could launch it with the UEFI shell
EFI boot loader information - srs5694 & skodabenz
[http://ubuntuforums.org/showthread.php?t=1849160](http://ubuntuforums.org/showthread.php?t=1849160)

---

### Post by soyuz_one on 2012-04-20
OK so I gave up and reformatted the drive by attaching it externally to a windows system in NTFS. Then proceeded with a fresh 12.04 install. I still have the same problem however!! I did choose a quick format, maybe that was my mistake. Again I let ubuntu's setup perform the partitioning. 

The output from gdisk is

Number  Start (sector)    End (sector)  Size       Code  Name
   1              34          195346   95.4 MiB    EF00  
   2          195347       217896518   103.8 GiB   0700  
   3       217896519       234441598   7.9 GiB     8200

---

### Post by soyuz_one on 2012-04-20
I looked into changing the bios settings. By changing the boot settings and turning on the diagnostic screen the issue is alleviated somewhat (at least ubuntu loads automatically now).

---

### Post by oldfred on 2012-04-20
If the partitions are not aligned you will have issues as it takes longer to clear mis-aligned partitions.

SSD's and new 4k drives need alignment.
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
srs5694's to show 8 sector alignment post #9
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)

---

### Post by soyuz_one on 2012-04-21
I've had trouble using gparted to align the partition /dev/sda1, the booting one. I've tried resizing and I've managed to get the ext4 and swap to start at their correctly aligned points but I cannot change the starting point of /dev/sda1. Gparted does not let me do it, simply stating:

"GNU Parted cannot resize this partition to this size. We're working on it!"

Also have you any advice on what to do after I've edited these points. Having looked at other pages, it seems I may have to edit fstab to get the UUIDs to match?

---

### Post by oldfred on 2012-04-21
If you just move partitions the UUID should not change. But if you delete & recreate then the UUIDs do change.

Usually you cannot move the start of a partition. But you shrink partition from left, then move the entire partition right.

Part of why I prefer to partition in advance as then there is no data to worry about if I want to make changes. Moving partitions can be slow depend on size. Always have good backups if you have any data you might want to save.

---

