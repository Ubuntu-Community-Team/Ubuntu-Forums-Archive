---
title: "Windows 7 Partition Not Recognized-Fdisk says overlapping parts-Fixparts doesn't work"
date: 2012-07-06
forum: General Help
---

### Post by lilproff on 2012-07-06
Hello, I am new to linux in general and have been trying to solve this problem for the past few days or so. I know there are several forum posts on this issue and am actually feeling extremely overwhelemed and exasperated about it all. I just want to install Lubuntu (dual boot it). Here what happened and what I've done.

[CENTER]
**The Problem: **[/CENTER]
1) I am running Lubuntu currently from a "live cd" (USB, got from netbootin I think its what it's called?). I have windows 7
2) I click Install Lubuntu and when the installer comes up it does not give me an option to download along side windows
3) I click other, it does not recgonize my partitions. (/dev/sda is unallocated)
4) Gparted also says my sda is unallocated
5) fdisk -lu does show my partitions and says they are overlapping

[CENTER]**What I've Done**[/CENTER]
1) Ran chkdsk (Wasn't working for the longest time, that took the majority of my past few days. ) Said everything was fine
2) Defragmented multiple times 
3) Used the repair disk for windows (its how I finally got chkdisk to work)
4) ran /FixMbr in under the repair disc command line 
5) I have installed fixparts and backed up my partition table and then clicked s which I've read helps fix this problem. When I clicked p afterwards the partitions where the same.

[CENTER]**An Issue**[/CENTER]

I am currently using a school laptop which isn't an issue, I mean its mine technically, but it has some Novelle network stuff which I am terrified of getting rid of and then having to pay a fine/for a new hard drive when I'll need access to it in the fall so....

1) Re-imaging my hard drive is the absolute last option

. 

**[CENTER]Required Data + Screenshots[/CENTER]**

**_[CENTER]fdisk -lu[/CENTER]_**

> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe08cb1bf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     2723839     1360896    7  HPFS/NTFS/exFAT
/dev/sda2         2723840   267491327   132383744    7  HPFS/NTFS/exFAT
/dev/sda3       267503040   312575759    22536360    7  HPFS/NTFS/exFAT
/dev/sda4       267498315   312560639    22531162+   7  HPFS/NTFS/exFAT

Partition table entries are not in disk order


**[CENTER]_Fixparts_[/CENTER]**
> ubuntu@lubuntu:~$ sudo fixparts /dev/sda
FixParts 0.8.1

Loading MBR data from /dev/sda

Problem: MBR partitions 3 and 4 overlap!

MBR command (? for help): p

** NOTE: Partition numbers do NOT indicate final primary/logical status,
** unlike in most MBR partitioning tools!

** Extended partitions are not displayed, but will be generated as required.

Disk size is 312581808 sectors (149.1 GiB)
MBR disk identifier: 0xE08CB1BF
MBR partitions:

                                                   Can Be   Can Be
Number  Boot  Start Sector   End Sector   Status   Logical  Primary   Code
   1      *           2048      2723839   primary     Y        Y      0x07
   2               2723840    267491327   primary              Y      0x07
   3             267503040    312575759   primary     Y        Y      0x07
   4             267498315    312560639   omitted     Y        Y      0x07

MBR command (? for help): s

MBR command (? for help): p

Disk size is 312581808 sectors (149.1 GiB)
MBR disk identifier: 0xE08CB1BF
MBR partitions:

                                                   Can Be   Can Be
Number  Boot  Start Sector   End Sector   Status   Logical  Primary   Code
   1      *           2048      2723839   primary     Y        Y      0x07
   2               2723840    267491327   primary              Y      0x07
   3             267498315    312560639   omitted     Y        Y      0x07
   4             267503040    312575759   primary     Y        Y      0x07



**_Computer Specs: _**
Thinkpad T420
160 gb hardrive
(not sure what else you'll need, let me know if anything)

I just want to install Lubuntu and do all of the wonderful frolicking that Linux users do! If it weren't for the possible fines I'd just put Lubuntu in place of Windows all together but I can't. Someone please help! I am about to pull my hair out! I am thinking there is more I can do with fixparts, but because of all of the horrible warning signs I see all over the internet, I'm terrible afraid of just playing around with it! Help!

---

### Post by flemur13013 on 2012-07-06
Does windows boot and run properly?

You have four partitions; I'm guessing that (you should label them):
/dev/sda1 is the win7 boot partition
/dev/sda2 is your C: drive with win7 installed. If so, Novelle is (probably) installed here.
/dev/sda3 and sda4 overlap and cause problems, and have what(?) on them?

My free advice is: 
 - do everything under windows.
 - use something like "partition wizard" to deal with NTFS partitions; you can run it from windows or from their boot disk. It's free.
 - save whatever is on sda3 and sda4 and then delete them.
 - if that doesn't work, check with your school about re-installing the Novelle stuff; I'd be surprised if they prevented or fined you for re-installing it; if you can do that, then reformat the whole disk or get a disk image from them (but perhaps that's what caused the original problem?  Did you mess with the partitions before having the problem? Does windows work OK?)

I've had linux disk tools screw up NTFS partitions in such that the only way I could fix them was to delete and recreate them. (they were usable but gave weird error messages - like "changes won't be applied until reboot" but were never applied - when trying to change anything).

---

### Post by oldfred on 2012-07-06
Fixparts cannot fix the overlapping issue as it does not know if the overlap belongs to sda3 or sda4. It looks like sda3 and sda4 start at almost the same sector and end on the same. Or the almost totally overlap. It does look like it will let you rewrite partition table with one or the other deleted if that is what you want.

If you have any important data try to back up from sda3 or sda4.

Under MBR(msdos) partitioning you can only have 4 primary partitions. You have four partitions, so you cannot create anymore. If you can delete sda4, you can convert one (and only one) primary partition to an extended partition which is a container for many logical partition. Linux will install and boot from logical partitions just fine.

With partition table corruption a lot of tools stop working as they do not know how to handle the issue.

If nothing else works and you backed up with sfdisk from your liveUSB, then you can manually edit that file and use it to reload a valid partition table. Anything else would be easier, but not even sure how you can delete when they overlap that much.

Using sfdisk to fix partition table problems - not without risk
[http://ubuntuforums.org/showthread.php?t=1192598](http://ubuntuforums.org/showthread.php?t=1192598)
Equivalent sfdisk values would keep the start point and convert the end point via the formula size = end - start + 1. 
Also fdisk -lu shows start & blocks, blocks * 2 also equals size in sectors

---

