---
title: "Recover damaged or corrupted flash drive"
date: 2011-10-04
forum: General Help
---

### Post by imhotep531 on 2011-10-04
I had a USB flash drive plugged into a hub that was yanked off my desk and disconnected. A file was open at the time and ever since then I get nothing when I plug this flash drive into a computer or hub. I've tried several different computers running various flavors of Windows. The incident happened on Windows 7.
 
Before the suggestions start flying I'd like to be real specific. No its not backed up. If it was I wouldn't be asking. I'm only interested in pursuing any methods for getting back into this drive via Linux. Trust me when I say I've pursued every avenue with Windows. I've tried several utilities as well as every possible means within Windows 7 and XP. I don't even get a balloon popping up saying the drive could not be recognized. So either this drive is corrupted to the point that Windows won't even show it in Disk Management or interact with it on any level (what I'm hoping is the case), or it is physically damaged and probably beyond any recovery aside from paying a professional service to resusitate electronically.
 
What, if anything, can I do with a live CD of Ubuntu to poke and prod this drive back to a point where I can get data off it again?

---

### Post by mikewhatever on 2011-10-04
Ubuntu Live CD is not exactly a recovery tool, but if you think it worthwhile, plug the drive in and see if anything happens.
Are you at all familiar with the Linux terminal?

---

### Post by imhotep531 on 2011-10-05
Yes I've spent a lot of time setting up 10 LTS server edition as a web server.  I have experience with SMB via Putty from a Windows machine and setting up port forwarding on my home router so I could access the Ubuntu server from elsewhere on the web.  Setting up RAID is another one.
 
What I'm not familiar with is how to mount a flash drive.  Assuming I'm able to access my busted flash drive using Ubuntu, how would I go about transferring those files to another flash drive, ensuring that its NTFS so I can then use them on a Windows machine later?

---

### Post by mikewhatever on 2011-10-05
By default, an external USB drive partitions are auto-mounted, and links appear in the left panel of the file browser. If that's the case, it would be easy to to copy paste the files, but I suspect that it's not going to be that simple.

Ubuntu will often refuse to mount a damaged file system, so if nothing happens when you plug the flash drive in, try running the commands:
```

sudo fdisk -l  #that's an L not one

dmesg | tail

```

If the flash drive is seen by fdisk, you should get an output similar to this:
```

sudo fdisk -l
Disk /dev/sdc: 2048 MB, 2048901120 bytes
64 heads, 62 sectors/track, 1008 cylinders
Units = cylinders of 3968 * 512 = 2031616 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ce2a4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1008     1999841    c  W95 FAT32 (LBA)

```

dmesg should provide some more info:
```
dmesg | tail
[145531.594133] scsi 4:0:0:0: Direct-Access     SanDisk  Cruzer Micro     0.1  PQ: 0 ANSI: 2
[145531.597343] sd 4:0:0:0: Attached scsi generic sg2 type 0
[145531.620079] sd 4:0:0:0: [sdc] 4001760 512-byte logical blocks: (2.04 GB/1.90 GiB)
[145531.620679] sd 4:0:0:0: [sdc] Write Protect is off
[145531.620695] sd 4:0:0:0: [sdc] Mode Sense: 03 00 00 00
[145531.620706] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[145531.625302] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[145531.625327]  sdc: sdc1
[145531.630262] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[145531.630280] sd 4:0:0:0: [sdc] Attached SCSI removable disk

```

If the drive is recognized, you could try fixing the file system (what was the file system?) or [using Photorec]("http://www.psychocats.net/ubuntucat/recoverdeletedfiles/"). If the drive is not recognized at all, I doubt there is anything Ubuntu CD can do.

---

### Post by imhotep531 on 2011-10-09
Mike, sorry it took so long for me to give this a try.  So I booted with a live CD and ran the commands as you suggested.  Here's what I get:

[CODEDisk /dev/sda: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x79fdeb5d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       15566   124930048    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x83043b6f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488380416    7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x83043b6f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488380416    7  HPFS/NTFS
][/CODE]

The two 500GB drives are my RAID1 array and the 128GB SSD is my main drive for the OS and applications.  So I'm wondering if that middle one that says "Partition 1 does not end on cylinder boundary" is the flash drive.  How can I test this and what is the next step in recovering files from it?  I don't remember what file system is on it.  It would probably be either FAT or NTFS since I first used it on a Windows machine, correct?

---

### Post by imhotep531 on 2011-10-10
Bump
 
If anyone has any advice on how to proceed I'd greatly appreciate it.  I feel like this flash drive can be revived I just don't know what the next step is.

---

