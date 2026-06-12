---
title: "How do I access and boot from second drive?"
date: 2010-10-21
forum: General Help
---

### Post by Chuck_N on 2010-10-21
p { margin-bottom: 0.08in; }  Hi,
 I have two 40-gig drives on a Compaq Presario SR1503WM. Ubuntu 10.04 Lucid Lynx is the boot system on sdb1.  Some time ago, I became unable to boot from sdb2 (win2K) and stopped trying.
   I have now installed Gparted (Gnome Partition Editor) and it shows me the following:   
 
[LIST=1]
[*]if I click on Gparted and choose 	Devices, I see sda and sdb both listed as 37+ gig.
[*]On the main window, however,  it 	shows sdb1 (which I assume is sda) as 35.7 gig (3Gig used), and 	sdb2, only as size 1.57Gig, with no indication how much is used or 	free.
[*]If I call up information on sbd2 	it indicates  File system: extended     Size: 1.57Gig      Status: 	Not busy (there are no mounted logical partitions)      Total 	sectors 3,297,282
[*]sdb1 Device information:  model: 	ATA WDC WD400AB-OOBV     size: 37.27Gig       Path: /dev/sdb      	Partition table:  msdos       Heads: 255      Sectors/track:  63     	   Cylinders: 4865 Total sectors:   78,156,225
[/LIST]
 Do you have any ideas on how to proceed to use that device again and to get capability to  boot-to-Windows drive?

---

### Post by AlphaLexman on 2010-10-21
> **Chuck_N said:**
> 
[LIST=1]
[*]On the main window, however,  it     shows sdb1 (which I assume is sda) as 35.7 gig (3Gig used), and     sdb2, only as size 1.57Gig, with no indication how much is used or     free.
[/LIST]
'sda' and 'sdb' should be your 2 hard drives. 'sda1' and 'sda2' would be two different partitions on the first hard drive. 'sdb1' and 'sdb2' are also two different partitions on the second hard drive. It looks like the first partition (sdb1) is your ubuntu, and the second partition is most likely a 'swap' partition for memory. 'sda1' shoould be your windows partition. It may not be mounted.

---

### Post by Mark Phelps on 2010-10-21
Rather than us having to guess what is what, how about opening a terminal, entering "sudo fdisk -lu" (that's a lowercase L, not a one), and posting the output back here.

---

### Post by Chuck_N on 2010-10-21
> **Mark Phelps said:**
> Rather than us having to guess what is what, how about opening a terminal, entering "sudo fdisk -lu" (that's a lowercase L, not a one), and posting the output back here.

okay, here it is. So what happened to my second drive? That used to be Win2K, secondary boot.  

Disk /dev/sda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders, total 78125000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000f3727

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    74823679    37410816   83  Linux
/dev/sda2        74825726    78123007     1648641    5  Extended
/dev/sda5        74825728    78123007     1648640   82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c64d7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    74864639    37431296   83  Linux
/dev/sdb2        74866686    78163967     1648641    5  Extended
/dev/sdb5        74866688    78163967     1648640   82  Linux swap / Solaris

---

### Post by Chuck_N on 2010-10-27
hello Mark,
care to look at this again?

---

### Post by Quackers on 2010-10-27
You seem to have Linux on both drives in very similar partition tables. No Windows there.
If you boot into whatever system you can, then run
```
sudo update-grub
```
in a terminal the second OS should show up, then be bootable.

---

### Post by Mark Phelps on 2010-10-27
Sorry, missed your reply ...

From the output, it now appears, at least structurally, that you have two nearly IDENTICAL drives!

Somehow, your Linux install got cloned to the second drive.

I don't personally use RAID, so I can't tell by looking at that output whether or not you have RAID implemented.  Two drives, identical in size and partitioning, tend to indicate RAID -- but that's not a given.  And, in your case, the partitioning is different -- slightly -- but different.

You can try using testdisk to recover the second drive to it's original state -- but others will have to help you with that as I've never had it work for me.  In my case, I've always used MS Windows-based utilities (GetDataBack and Recover My Files) to recover from damaged NTFS partitions.

---

### Post by Chuck_N on 2010-10-27
[COLOR=Red]> **Mark Phelps said:**
> Sorry, missed your reply ...

From the output, it now appears, at least structurally, that you have two nearly IDENTICAL drives![/COLOR]> **Mark Phelps said:**
>  [COLOR=Red]

Somehow, your Linux install got cloned to the second drive.[/COLOR] [COLOR=Red]

I don't personally use RAID, so I can't tell by looking at that output whether or not you have RAID implemented.  Two drives, identical in size and partitioning, tend to indicate RAID -- but that's not a given.  And, in your case, the partitioning is different -- slightly -- but different.[/COLOR] [COLOR=Red]

You can try using testdisk to recover the second drive to it's original state -- but others will have to help you with that as I've never had it work for me.  In my case, I've always used MS Windows-based utilities (GetDataBack and Recover My Files) to recover from damaged NTFS partitions.[/COLOR] 


ah yes, checked my notes..... for some reason the windows alternate boot quit working; I didn't have a disk to fix it; probably reformatted it, intending to use it as a data disk/backup disk for sba. Problem is, apparently it has a system partition, which wasn't necessary.  Also, I have no idea how to USE the drive.  Can I use some backup program to write to sdb?
Yes, I updated Grub and was able to boot from sdb.

---

