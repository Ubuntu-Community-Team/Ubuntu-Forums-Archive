---
title: "HFS+ disk mounts but no longer writable, but CAN'T DO fsck.hfsplus"
date: 2011-11-26
forum: General Help
---

### Post by youWho on 2011-11-26
Hi. I'd be grateful for your thoughts:

I have an external disk, formatted HFS+, connected by USB2. Journaling is off and so I could mount it read/write. Even though I'm always careful to unmount it before disconnecting it sometimes I get a message saying its read only; then I have to do fsck.hfsplus, which has always fixed it.

But all of a sudden it only mounts read only, and if I use
# sudo fdisk -l
to try to determine which path to use for fsck.hfsplus I get this: 
"Disk /dev/sdb doesn't contain a valid partition table"
If I try to use fsck.hfsplus by trying for example /dev/sdb1 (just to try) it refuses to do anything. Also strange is that it still works fine for reading.

So I'm stuck. I'd like to be able to fix this and mount it read/write again, but I don't know how. Any advice? (Thanks!!!)

I should say that that morning, before it bacame read only, when starting the computer fsck did its normal every-30-boots check, but what's odd is that it had done that too the day before and I certainly didn't reboot 30 times ;-). Normally I never boot the computer with the external drive already connected but that morning I forgot; could this matter??

This is Ubuntu Studio Natty 64 bit

---

### Post by coffeecat on 2011-11-26
> **youWho said:**
> 
# sudo fdisk -l
to try to determine which path to use for fsck.hfsplus I get this: 
"Disk /dev/sdb doesn't contain a valid partition table"

Which version of Ubuntu are you running? When I plug a hfs+ formatted drive into this Oneiric/11.10 system and run fdisk, I get:

```
WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.
```

But then goes on to say:

```
Disk /dev/sdc: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1   117210239    58605119+  ee  GPT

```

The versions of fdisk that came in earlier versions of Ubuntu were much more terse in their output when confronted with a GUID partition table and you will probably have a GPT table with that drive if it was formatted in a Mac.

Try parted - you might have to install it - with:

```
sudo parted -l
```

Which in my case gives me:

```
Disk /dev/sdc: 60.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name                  Flags
 1      20.5kB  210MB   210MB   fat32        EFI System Partition  boot
 2      210MB   59.9GB  59.7GB  hfs+         hfs+
```

My hfs+ partition is sdc2, not sdc1, as fdisk is trying to tell me.

---

### Post by youWho on 2011-11-26
Hi. Thanks for your help.

> **coffeecat said:**
> Which version of Ubuntu are you running?

I'm using Ubuntu Natty, 64 bit. Strictly speaking it's Ubuntu Studio Natty. I doubt that matters, but I mention it in case it might.

I probably tried too hard to keep my question minimal, and so didn't explain enough. But the thing is that this has occurred before---that the disk becomes somehow futzd and no longer allows writing. In the past I've always been able to fix it with fsck.hfsplus, first doing fdisk -l to see which partition to fix with fsck.hfsplus, and I haven't changed anything in the meantime. That is, unless some part of a regular update could have changed something relevant and I didn't know.

For me "GPT' and "GUID Partition Table" are new terms (I'll go try to learn about that now...) But re your comment I see that I have parted installed.

> **coffeecat said:**
> Try parted - you might have to install it - with:

parted -l gives this output (the parts relating to that disk):

Model: ST910082 3A (scsi)
Disk /dev/sdb: 100GB
Sector size (logical/physical): 512B/512B
Partition Table: mac

Number  Start   End     Size    File system  Name                  Flags
 1      512B    32.8kB  32.3kB               Apple
 2      32.8kB  61.4kB  28.7kB               Macintosh
 3      61.4kB  90.1kB  28.7kB               Macintosh
 4      90.1kB  119kB   28.7kB               Macintosh
 5      119kB   147kB   28.7kB               Macintosh
 6      147kB   410kB   262kB                Macintosh
 7      410kB   672kB   262kB                Macintosh
 8      672kB   934kB   262kB                Patch Partition
10      135MB   22.9GB  22.8GB  hfs+         Apple_HFS_Untitled_2
12      23.0GB  100GB   77.0GB  hfs+         Apple_HFS_Untitled_3

I don't understand what to glean from it though. The last 2 lines seem to be what I know to be the 2 partitions the disk was formatted (on a now dead Mac) to have; I had formatted it to have a 20GB and a 75GB or so partition; the disk is a 100GB disk.

But what I don't understand is what to do with this information. Can I use this with fsck.hfsplus somehow??? Sorry for the continued question but thanks for your help.

[edit] I just now tried "sudo parted /dev/sdb check" then when it asked me "Partition number?" I tried answering 1 then again with 2 and both times it answered "Error: Could not detect file system."
But like I say, the disk is working---just in read only mode. I don't get it.

Just generally I don't know what to do, and so thanks for any continued advice. But may I ask: is it possible that when fsck ran as Ubuntu was starting up the other day that it somehow deleted or re-wrote or modified the MBR or some other part of the external drive, updating it to, or assuming the existence of (or some other thing) a new GUID type of system??? As you can probably tell, I'm using terms I don't particularly understand here, but I'm learning. Thanks. [another edit] So I've just now been reading about GUID on Wikipedia and I guess that my last question was probably way off, but I donno.

If you have any advice... Thanks again.

---

### Post by coffeecat on 2011-11-26
You have an old APM partition table on that drive. It's a bit thin, but here's the wikipedia page for APM:

[http://en.wikipedia.org/wiki/Apple_Partition_Map](http://en.wikipedia.org/wiki/Apple_Partition_Map)

The APM was used on Macs with the old PPC CPUs. When they introduced Intel CPUs - or it may have been when Tiger came out - Apple switched to GUID partition tables. I must admit I know next to nothing about APM partition tables. All I know - from playing with an old PPC Mac with Panther - is that an APM looks mighty odd when you plug it into a Linux system. I don't think I'm going to be much help here, except...

Do you have access to a Mac? It's probably better trying to repair a MacOS filesystem with Mac utilities. Also - how long ago was that drive formatted? You can format drives with APT with newer versions of MacOSX, but it's not the default. If you can rescue the data with a Mac, it might be time to reformat the drive, or even replace it.

By the way, mbr refers to the master boot record which is a feature of the mbr or ms-dos partition table.

---

### Post by youWho on 2011-11-26
Hi and thanks again. As you said, the Wikipedia article about that doesn't have much, but thanks for helping with this.

Indeed the disk was formatted a long time ago, around 2003 I'd say. It was the replacement I put into the iBook I had when the original drive collapsed. And indeed I used OSX Panther on that Mac. The iBook itself collapsed some time ago and I have no other Mac access. Except of course asking a friend.

Anyway what's strange to me is the fact that this drive was capable of being read/write with this very same Ubuntu system, everything the same as it is now.

If anybody else has any insight into this particular situation please let me know...

---

