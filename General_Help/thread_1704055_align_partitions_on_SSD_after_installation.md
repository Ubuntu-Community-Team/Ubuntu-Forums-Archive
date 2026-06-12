---
title: "align partitions on SSD after installation"
date: 2011-03-10
forum: General Help
---

### Post by meijer.o on 2011-03-10
I use Ubuntu 10.10 on an Intel SSD, upgraded from 10.4. The partitions on the SSD are not aligned. Can someone tell me how to align after installation. Can I resize them with a life cd? (I tried this and it did not work.) Can I e.g. create a backup with remastersys and recreate the partitions (I know how to create aligned partitions) and then reinstall the backup?

How do I restore grub?
Does remastersys support grub2?
Can I use ext4 with remastersys?

Can someone give me advice?

Thanks for your help,

Otto Meijer

---

### Post by Ranko Kohime on 2011-03-10
What exactly do you mean by them not being "aligned"?

---

### Post by meijer.o on 2011-03-10
root@meijer:~# fdisk -H 32 -S 32 -lu /dev/sda

Disk /dev/sda: 80.0 GB, 80026361856 bytes
32 heads, 32 sectors/track, 152638 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00011a54

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    14649343     7323648   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2        14649344   154298367    69824512   83  Linux
Partition 2 does not end on cylinder boundary.
/dev/sda3       154300414   156153855      926721    5  Extended
Partition 3 does not end on cylinder boundary.
/dev/sda4       156153856   156301311       73728    b  W95 FAT32
Partition 4 does not end on cylinder boundary.
/dev/sda5       154300416   156153855      926720   82  Linux swap / Solaris
root@meijer:~# 

These partitions are not alligned.

---

### Post by Ranko Kohime on 2011-03-10
SSD's either don't have cylinders, or if they do, they are merely for compatibility with software expecting cylinders, as in a rotating-platter HDD.

Unless that's causing some issue, I'd leave it alone.

---

### Post by meijer.o on 2011-03-10
It can certainly help to align partitions, if you use a SSD. See e.g. this post [http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment&p=373226&viewfull=1#post373226](http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment&p=373226&viewfull=1#post373226).

I managed anyway. After installing

See:
root@meijer:~# fdisk -H 32 -S 32 -lu /dev/sda

Disk /dev/sda: 80.0 GB, 80026361856 bytes
32 heads, 32 sectors/track, 152638 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00011a54

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    19534847     9766400   83  Linux
/dev/sda2        19534848   154301439    67383296   83  Linux
/dev/sda3       154301440   156156927      927744   82  Linux swap / Solaris
/dev/sda4       156156928   156301311       72192   ef  EFI (FAT-12/16/32)

Best regard,

Otto Meijer

---

### Post by oldfred on 2011-03-10
Do not mix up the old CHS alignment which has been obsolete for years with LBA and the new sector alignment.

srs's to show 8 sector alignment
$ sudo parted /dev/sda unit s print

First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of RAID arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)

---

### Post by srs5694 on 2011-03-10
Oldfred is correct. In your original post, meijer.o, all your partitions began on 2048-sector boundaries (except for the extended partition, which is irrelevant). The start points of the partitions are the only points that are important for the alignment issues; the end points are irrelevant. Also, as oldfred says, some types of modern disks need alignment on 8-sector or larger power-of-2 multiples of sectors, *not* on "cylinder" values, which have been fictitious for years and are completely meaningless for SSDs. Thus, fdisk's complaints about partitions not ending on cylinder boundaries are deceptive because this issue has been unimportant for about two decades.

Your new configuration is also probably OK; all of your new partitions begin on 1024-sector boundaries, which is probably OK with modern SSDs, although you'd need to check the specs to be absolutely positive of that. (The 2048-sector boundary that has been adopted as a standard is comfortably higher than what most modern disks require, but details vary from one disk to another.)

FWIW, your new configuration includes an EFI System Partition as partition #4. This is almost certainly incorrect. This partition type is reserved for use to hold Extensible Firmware Interface (EFI) drivers and boot loaders on EFI-based computers such as Intel-based Macs. Few PCs support EFI, and those that do would normally be partitioned using the GUID Partition Table (GPT) rather than the Master Boot Record (MBR) system your disk uses. If you're using that partition for data exchange with a Windows installation on another disk, you should probably change it from 0xEF to 0x0C.

I'll also point out that you've now got four primary partitions, and they're crammed in with no space between them. This will make it difficult to resize and create new partitions in the future, should the need arise. If you're already using the disk, it may be simplest to just leave that aspect alone for the moment and deal with any problems in the future. If not, though, you might want to consider repartitioning, making just one or two partitions primary and making the rest of them logical partitions inside an extended partition, as you had in your first setup. Alternatively, you could convert the disk from MBR to GPT form; GPT doesn't use the primary/extended/logical distinction that's so important for MBR. Linux can boot from GPT disks, but Windows can't, so if you intend to boot Windows from this disk, such a conversion is inadvisable. Linux boots fine from GPT, though, and Windows Vista and later can read GPT disks as data disks just fine.

---

### Post by meijer.o on 2011-03-10
Dear srs5694,

Thank you for the replying. So I did the work in vain. At least I learned something. I need the efi partition indeed. It is used by the bios, system diagnostic utilities of my HP ProBook 4510s

Best regards,

otto meijer

---

### Post by Riot@ct on 2011-05-17
But if I want instal Ubuntu\Kubuntu 11.04 on a new SSD (Crucial C300), must I align manually the partition or not?

Thanks!

---

### Post by oldfred on 2011-05-17
You need to check with the vendor, but most newer partitioning tools use 2048 as the start sector.

While an Arch link, it has a good discussion of SSD's.
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

---

### Post by Riot@ct on 2011-05-17
> **oldfred said:**
> You need to check with the vendor, but most newer partitioning tools use 2048 as the start sector.

While an Arch link, it has a good discussion of SSD's.
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
Why I must to check with the vendor? :confused:
What uses Kubuntu\Ubuntu partitioning tools as start sector?

---

