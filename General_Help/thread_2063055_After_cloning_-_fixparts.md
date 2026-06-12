---
title: "After cloning - fixparts"
date: 2012-09-26
forum: General Help
---

### Post by gsedej on 2012-09-26
Hi!

Is it possible to use FixParts to shrink free extended partition that goes over end of disk?

the story:
I wished to clone disk A 320GB to disk B 320GB, but disk B was few MB smaller. On disk A I had last partition SWAP inside extended.
Even though I deleted last partition, Clonezilla still didn't want to clone it, so i just dd-it from A to B.

Ubuntu was working on disk B, but gparted didn't wish to touch it disk, because extended partition was over end of disk.
I used FixParts (just recompute and write). Gparted did see disk, but when I wanted to create swap partition, it always failed. Ubuntu Disk utility didn't show me free space in the end at all.
(something like kernel could not access... disk busy).

(in the end shrined partition on A, but it was not optimal)

---

### Post by coffeecat on 2012-09-26
Post moved to own thread. It's best to start your own threads. The thread you posted in had not been posted to for a long time.

I've used fixparts to correct an extended partition where the partition table showed this as going beyond the physical end of the drive, if that's what you mean. You might find the author's tutorial helpful:

[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by gsedej on 2012-09-26
Thanks for maintenance!

I already red man and web page. The only think you can do is option "c" to recalculate which does the thing, but gparted and disk tool does not wish to work with partition. 

Gparted ouptut:
[FONT="Courier New"]libparted messages
Error informing the kernel about modifications to partition /dev/sda5 - Device or resource busy. This means Linux won't know about any changes you made to /dev/sda5 until you reboot- so you shouldn't mount ti or use it in any way before rebooting.
failed to add partition 5 (Device or resource busy)
(no dmesg output)[/FONT]

Restart does not help. I used livecd, so partition was not mounted or used in any way.

---

### Post by oldfred on 2012-09-26
Do you still have both drives plugged in? They will have duplicate UUIDs and that greatly confuses everything.

Post this:

sudo fdisk -lu

# To clear cache and get new view (in code tags to preserve formatting):
sudo blkid -c /dev/null -o list

---

### Post by gsedej on 2012-09-27
Hi,

thanks for reply. I don't have time to fix this disk, because I already cloned others and also don't wish to have one pc that is a bit different.
Anyway, if someone else will need it.

fdisk
```
ubuntu@ubuntu:~$ sudo fdisk -lu
Disk /dev/sda: 320.1 GB, 320071851520 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625140335 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000138a2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   204802047   102400000    7  HPFS/NTFS/exFAT
/dev/sda2       204802048   409602047   102400000    7  HPFS/NTFS/exFAT
/dev/sda3       409604095   621045759   105720832+   f  W95 Ext'd (LBA)
/dev/sda4       621045760   625139711     2046976   83  Linux
/dev/sda5       409604096   621045759   105720832   83  Linux
```

blkid
```
ubuntu@ubuntu:~$ sudo blkid -c /dev/null -o list 
device                    fs_type    label       mount point                   UUID
--------------------------------------------------------------------------------------------------------------------
/dev/loop0                squashfs               /rofs                         
/dev/sda1                 ntfs       win7        (not mounted)                 03F0074124D85344
/dev/sda2                 ntfs       data-ntfs   (not mounted)                 0DEABCCE444A90B1
/dev/sda4                 swap       swap        <swap>                        c047c595-f6f2-4136-95af-314e67fcc554
/dev/sda5                 ext4                   (not mounted)                 91eced2a-50ce-4d7a-8649-883638368551
/dev/sr0                  iso9660    Ubuntu 12.04 LTS amd64 /cdrom
```

And fixparts print
```
ubuntu@ubuntu:~$ sudo fixparts /dev/sda
FixParts 0.8.1
Loading MBR data from /dev/sda
MBR command (? for help): p

** NOTE: Partition numbers do NOT indicate final primary/logical status,
** unlike in most MBR partitioning tools!
** Extended partitions are not displayed, but will be generated as required.
Disk size is 625140335 sectors (298.1 GiB)
MBR disk identifier: 0x000138A2
MBR partitions:                                                   Can Be   Can Be
Number  Boot  Start Sector   End Sector   Status   Logical  Primary   Code
   1      *           2048    204802047   primary              Y      0x07
   2             204802048    409602047   primary              Y      0x07
   4             621045760    625139711   primary              Y      0x83
   5             409604096    621045759   logical     Y        Y      0x83
```


What should one do if gets in similar situation? Does numbers look wrong, or just gparted does not like?
(I had to wipe this disk)

---

### Post by oldfred on 2012-09-27
I do not see any issue with partition table, others may be able to see something?

---

