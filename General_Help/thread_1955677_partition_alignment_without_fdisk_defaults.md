---
title: "partition alignment without fdisk defaults"
date: 2012-04-09
forum: General Help
---

### Post by stlu on 2012-04-09
Hi,

I came across the change in linux fdisk.  In 11.10, the default start sector for a new partition is 2048.  I accustomed to the earlier value of 63 in older versions.  I wanted to go back to 63, since I don't like all the unallocated sectors.

After reading about possible reasons for the change, the main one seems to be the recent arrival of some drives with 4096-byte physical sectors.  Starting at sector 63 causes misalignment of the partitions in these drives, slowing things down.

So, after searching around, I can't understand why they want to start at sector #2048.  All that is needed is a multiple of 8, right?  The only other suggested start start sector was 64, which is the start of the 9th 4k sector, but I suspect the author was restricted by the lower limit of 63 sectors in the older version of fdisk, and he could not choose a lower multiple.

Now that I know that 63 is also silly, I want to go even lower!

I am not limited by fdisk(I will be using "parted" instead), and I want to use all sectors possible.  I learned that some unallocated sectors are used for backup copies of the FAT in msdos filesystems, but this unallocated space has no use in ext2.   It seems I could even start at sector 1.  Well, on a 4k sector drive, that would still be misaligned, so I want to hit the lowest boundary of 4k sectors.  Unless my math is wrong, sectors 0-7 comprise the first 4k physical sector, therefore the lowest I can start is sector 8.  Is that a sound decision?

Let me know if there is anything that would make this a bad choice.  I am not using any other filesystem then ext2/3/4, so compatibility with windows is not my concern.

---

### Post by Herman on 2012-04-10
If you're booting with GRUB you'll probably want to leave at least 48 sectors after the MBR for GRUB to embed its core.img in.

An easy way to go back to the old cylinder boundary alignment (sector 63) would be to download an older version of gparted live CD or an old version of Ubuntu Live CD and use either of those to do your partitioning work.

---

### Post by Cheesemill on 2012-04-10
The 2048 refers to starting at 2048KB, not the 2048th sector so you are only losing 2MB of space.

---

### Post by oldfred on 2012-04-10
Cylinders have not been used since drives went over 8GB. LBA or large block allocation is  the standard since.

First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of RAID arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)
srs's to show 8 sector alignment
$ sudo parted /dev/sda unit s print

I am only using Linux on all new drives, so I use gpt which is a new partitioning scheme. 40 then is often the first sector, although 2048 is used as the standard. With gpt you have no space after the MBR to worry about but do need a bios_grub so there is a place for core.img.

---

### Post by stlu on 2012-04-20
> **Herman said:**
> If you're booting with GRUB you'll probably want to leave at least 48 sectors after the MBR for GRUB to embed its core.img in.

An easy way to go back to the old cylinder boundary alignment (sector 63) would be to download an older version of gparted live CD or an old version of Ubuntu Live CD and use either of those to do your partitioning work.
Thanks for the note about GRUB2 needing 48 sectors.  In my case, this is a storage drive that will have no OS(no GRUB), so I still want to use up those sectors.

> **Cheesemill said:**
> The 2048 refers to starting at 2048KB, not the 2048th sector so you are only losing 2MB of space.
That's absolutely wrong, the sectors are 512 bytes in size.  The unallocated sectors (0-2047) represent 2048*512 sectors, or 1MB lost.  And I don't want to lose it unless a drive with no OS needs that empty space for a good reason.

---

### Post by stlu on 2012-04-20
> **oldfred said:**
> Cylinders have not been used since drives went over 8GB. LBA or large block allocation is  the standard since.

First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of RAID arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)
srs's to show 8 sector alignment
$ sudo parted /dev/sda unit s print

I am only using Linux on all new drives, so I use gpt which is a new partitioning scheme. 40 then is often the first sector, although 2048 is used as the standard. With gpt you have no space after the MBR to worry about but do need a bios_grub so there is a place for core.img.

Dear oldfred,

you done good!

Ref: [http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)

> In principle, you can start the first partition with a sector number as low as 8 for proper alignment; however, it's best to start the first partition at 64 or higher to leave room for boot loader code

So I can start my partition at sector 8, my math was right.  But only for a drive which wont have any OS.

```
$ sudo parted /dev/sdd
(parted) unit s

(parted) mklabel msdos

(parted) mkpart
Partition type?  primary/extended? p
File system type?  [ext2]?
Start? 8s
End? -1s

(parted) print
Model: WD Ext HDD 1021 (scsi)
Disk /dev/sdd: 1953519616s
Sector size (logical/physical): 512B/512B    #NOT trusting this info...
Partition Table: msdos

Number  Start  End          Size         Type     File system  Flags
 1      8s     1953519615s  1953519608s  primary                    



$ sudo fdisk /dev/sdd

Command (m for help): u
Changing display/entry units to sectors

Command (m for help): p

Disk /dev/sdd: 1000.2 GB, 1000202043392 bytes
255 heads, 63 sectors/track, 121600 cylinders, total 1953519616 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000d0b22

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               8  1953519615   976759804   83  Linux

Command (m for help): v
7 unallocated sectors

```

---

