---
title: "Advanced Format Alignment of Hard Disks"
date: 2011-05-27
forum: General Help
---

### Post by imwithid on 2011-05-27
I thought that alignment of 4096-byte sector Advanced Format hard drives was automatically taken care of via Gparted or Disk Utility until I bought a Hitachi HTS547575A9E384 (Travelstar 5K750) and saw that Disk Utility showed my partitions to be out of alignment[IMG]http://i51.tinypic.com/2i7prvp.png[/IMG]. I then realized that my WD, which I had bought a few months ago, probably had its jumper set to emulate a 512-byte sector legacy drive (512e) and is probably not set to the AF setting.

Straight to the problem.

I've searched many sites, some of which suggest using fdisk (others the proprietary software of the hard drive's manufacturer). It is essential that one change the arguments prior to changing the partition table as there is no way back (yet, as far as I know) without having to move data to another drive and starting all over:

```
sudo fdisk -b 4096 -u /dev/sdx
```

This argument should then set the sector definition to 4096-bytes from the default 512-bytes and display/entry units to sectors. However, this seems not to be the case upon writing to the disk:

```
dm@dm-desktop:~$ sudo fdisk -b 4096 -u /dev/sdb
Note: sector size is 4096 (not 512)

WARNING: DOS-compatible mode is deprecated. It's strongly recommended to
         switch off the mode (command 'c').

Command (m for help): p

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 11400 cylinders, total 183143646 sectors
Units = sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000a8c8d

   Device Boot      Start         End      Blocks   Id  System

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 1
First sector (63-183143645, default 64): 
Using default value 64
Last sector, +sectors or +size{K,M,G} (64-183143645, default 183143645): 8000063

Command (m for help): t
Selected partition 1
Hex code (type L to list codes): 7
Changed system type of partition 1 to 7 (HPFS/NTFS)

Command (m for help): p

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 11400 cylinders, total 183143646 sectors
Units = sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000a8c8d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              64     8000063    32000000    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.
```

My disk is now aligned, however, it should be partitioned as a 32 GB partition with 4096-byte sectors but instead is partitioned to 4.1 GB with logical sectors defined as 512-bytes:

```
dm@dm-desktop:~$ sudo fdisk -l /dev/sdb

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
251 heads, 9 sectors/track, 648583 cylinders
Units = cylinders of 2259 * 512 = 1156608 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000a8c8d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3542     4000000    7  HPFS/NTFS
```

Has anyone any suggestions as to what is wrong and how it can be fixed?

---

### Post by imwithid on 2011-05-27
After about six hours of experimenting with many programs and methods, I suppose some of the error lies in my interpretation of 'units'.

This is somewhat ambiguous as the output will be shown in *'x'* units, however, inputs are set at fixed and arbitrary units, in this case 512-byte sectors (if using the sectors option).

In the end, by using fdisk to align and gparted to format and fix the partition, I was able to manually align my drive. Although the partitions are aligned, does anyone know whether the 512-bytes logical sector affects performance given that it should really be 4096-bytes (since aligning problem is solved, is there a translation performance penalty internally?)

---

### Post by Grenage on 2011-05-27
> **imwithid said:**
> After about six hours of experimenting with many programs and methods, I suppose some of the error lies in my interpretation of 'units'.

This is somewhat ambiguous as the output will be shown in *'x'* units, however, inputs are set at fixed and arbitrary units, in this case 512-byte sectors (if using the sectors option).

In the end, by using fdisk to align and gparted to format and fix the partition, I was able to manually align my drive. Although the partitions are aligned, does anyone know whether the 512-bytes logical sector affects performance given that it should really be 4096-bytes (since aligning problem is solved, is there a translation performance penalty internally?)

As far as I am aware there isn't really a penalty as long as he partitions are correctly aligned; so if you're starting a partition on a division of 8 (64), you should be good.

I personally found [this]("http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html?ca=dat-") IBM page to be very informative some time ago.  Many of the utilities have been updated, but the fdisk info for future partitions is good.

---

### Post by srs5694 on 2011-05-27
I'd like to address a couple of critical misunderstandings in the first post. I think you figured them out later, but I just want to be sure:


[list]
[*]You should ***NOT*** attempt to adjust the sector size using fdisk's -b option! Doing so will produce a completely unusable partition table. Advanced Format disks lie about their sector size and "translate" themselves, so trying to do the "translation" yourself in fdisk would be like doing an English-to-metric conversion twice.
[*]AFAIK, no WD drive includes a jumper to do any sort of translation or to enable or disable Advanced Format operation; what they do have is a jumper to adjust the sector references by one, so that when a disk utility creates a partition on sector 63 (unaligned), it really begins on sector 64 (aligned). No matter how this jumper is set, the disk still uses 4096-byte sectors and pretends to have 512-byte sectors. I do *not* recommend using this jumper setting. It's better to align the partitions correctly in software. The trouble with the jumper is twofold: First, if you use it and then want to create multiple partitions, you'll have to manually align all the subsequent partitions in an unusual way (namely, divisible-by-8 minus 1). Second, if you use this setting and then forget it, if you repartition the disk with more modern utilities, you'll be aligning things improperly.
[/list]


The Disk Utility program you used sometimes creates false alarms about alignment. IIRC, this sometimes happens because it considers the alignment of extended partitions to be important, but it's not; only primary and logical partitions matter, since they're the only ones that hold data structures that are sized in such a way that alignment is important.

The best way to check your alignment is to use fdisk or parted (or gdisk, if you use GPT disks) to view your partition start points with sector precision, as in:

```
$ **sudo fdisk -lu /dev/sdb**

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00022117

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63      192779       96358+  83  Linux
/dev/sdb2         1012095   625137344   312062625   8e  Linux LVM
/dev/sdb3          192780     1012094      409657+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

This example's partitions are *not* properly aligned, since none of the start points begin on sector numbers that are divisible by 8. (In this case that's fine, since this isn't an Advanced Format disk.)

---

### Post by psusi on 2011-05-27
Your screen shot shows NTFS partitions, which were presumably created by Windows XP, not gparted or the disk utility, which is why it is misaligned.  Delete the partitions and create them with gparted or the disk utility and they will be properly aligned.

---

### Post by imwithid on 2011-05-27
> **psusi said:**
> Your screen shot shows NTFS partitions, which were presumably created by Windows XP, not gparted or the disk utility, which is why it is misaligned.  Delete the partitions and create them with gparted or the disk utility and they will be properly aligned.

They were created using GParted on a new, sealed, out of static bag disk. I used Disk Utility as a double check for alignment, whose outcome was posted in the above image. It seems as though GParted does not always align properly partitions along the 4096 sector moduli or else Disk Utility does not or cannot accurately check for alignment.

---

### Post by imwithid on 2011-05-27
@srs5694,

I thought I was certain as to what I was doing, however, this Hitachi drive threw me into some doubt or conflict, I would rather say, as it does not seamlessly translate the 512 / 4096 byte sector adjustment as finely as the WD.

After the fact, I removed the WD from it's casing and noticed that it had no jumpers which led me to realize that it is the firmware that is taking care of the emulation. I looked up the jumper settings and it is as you have said (with the addition of a couple of other features; low power, spread spectrum clocking (SSC), etc.; features that few should manipulate and only on a need basis).

I understand the theory behind alignment, but I think it's the transitional fixes that at times cause conflict for those who are prepared to tackle the problem themselves. Although I understand, now, why WD set up their AF drives in this manner, I would rather leave it as an option to emulate the 512-byte sector. I hope a firmware release is made soon to allow users to do as they wish. There must be a minor performance loss for this emulation feature, although it's most likely so marginal that the trade off makes it worthwhile for the majority not technically willing or inclined.

---

### Post by srs5694 on 2011-05-28
> **imwithid said:**
> They were created using GParted on a new, sealed, out of static bag disk. I used Disk Utility as a double check for alignment, whose outcome was posted in the above image. It seems as though GParted does not always align properly partitions along the 4096 sector moduli or else Disk Utility does not or cannot accurately check for alignment.

Until about 1-1.5 years ago, GParted did not have an option to align to 1 MiB boundaries. Thus, depending on the ages of the software that was used, it's possible that it wasn't properly aligned when created but a newer version of GParted would squawk about the partitions that its earlier version created. Also, as I noted in my earlier post, GParted sometimes produces false alarms about alignment. Thus, you can *not* trust a GParted claim that a partition is improperly aligned. The *only* way to be *sure* your disk is properly (or improperly) aligned is to check the partition start points using a partitioning tool that presents this data with sector (not cylinder) precision.

Another point: Proper alignment is *not* along "4096 sector moduli"; it's *8-sector* (4096-*byte*) alignment. Most utilities today align to 1 MiB (2048-sector) boundaries because this value is divisible by 8 and it also guarantees proper alignment for various other technologies, like some types of RAID array, that have their own alignment requirements. (Of course, since 4096 is divisible by 8, aligning to a 4096-sector boundary will be correct, but you'll waste a bit more disk space that way.)

> I thought I was certain as to what I was doing, however, this Hitachi  drive threw me into some doubt or conflict, I would rather say, as it  does not seamlessly translate the 512 / 4096 byte sector adjustment as  finely as the WD.

They both do it in exactly the same way, AFAIK, although if the Hitachi drive doesn't have a jumper to translate the sector numbers by one unit, that makes them simpler in that one respect. Aside from that jumper issue, there's no issue of one's adjustment being "finer" than the other. In particular, you should *not* assume that the warning GParted gave you has anything at all to do with a WD-vs-Hitachi difference. GParted sometimes issues such warnings even on disks that don't use Advanced Format at all.

> Although I understand, now, why WD set up their AF drives in this  manner, I would rather leave it as an option to emulate the 512-byte  sector. I hope a firmware release is made soon to allow users to do as  they wish.

I wouldn't expect a firmware update to enable you to use the disk as a 4096-byte-sector drive. I expect that drives that present their true 4096-byte sectors to the OS will eventually make it to market, but I find it hard to believe that a manufacturer would go to the effort of making such a firmware upgrade available; it's be a support nightmare.

---

### Post by mexicanseaf00d on 2011-05-30
I don't want to start another thread, as it appears to fit in here - 

*Is it possible to re-align a partition without data loss?* There's a lot of stuff on that partition, and no place to back it up atm. Its a WD WD7500KPVT notebook HD.

```
sudo fdisk -lu /dev/sda

Platte /dev/sda: 750.2 GByte, 750156374016 Byte
255 Köpfe, 63 Sektoren/Spur, 91201 Zylinder, zusammen 1465149168 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xc54c36cc

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sda1            2048    40964095    20481024   83  Linux
/dev/sda2        40965750  1380160214   669597232+  83  Linux
Partition 2 does not start on physical sector boundary.
/dev/sda4      1456599038  1465147391     4274177    5  Erweiterte
Partition 4 does not start on physical sector boundary.
/dev/sda5      1456599040  1465147391     4274176   82  Linux Swap / Solaris

```

sda2 is off by 1024 bytes (disk utility says that). Does that even matter? Or is my drive just slow anyway? ;) IIRC, I told gparted to align to sectors when I installed the system.

---

### Post by srs5694 on 2011-05-30
> **mexicanseaf00d said:**
> I don't want to start another thread, as it appears to fit in here - 

It's generally best to start a new thread rather than "hijack" an existing one. Trying to solve two problems in one thread can lead to confusion, and even problems that seem similar on the surface can be very different.

That said, your question is straightforward, so I'll give you one answer. If you need more advice, please start your own thread....

*> Is it possible to re-align a partition without data loss?*

Yes. Use GParted and tell it to align to 1 MiB boundaries. The usual caveats about moving the start of a partition apply, though, especially since you'll necessarily be moving the start of the partition rather than the end. Backing up the partition before moving is advisable.

---

### Post by mexicanseaf00d on 2011-05-30
thanks!

---

