---
title: "Recover files on Linux drive from Windows"
date: 2009-12-11
forum: General Help
---

### Post by t20t on 2009-12-11
Hi, first of all, I just want to say I am totally newbie in Linux.  Only tried the live cd once in a blue moon.  Anyway, I'm trying to get the files off a laptop that had Linux on it.  The owner told me it was running ubuntu linux.  I connected the hard drive to an ide-to-usb adapter and plugged it into my Vista/Win7 PCs.  Windows see the drive in disk management with two partitions, but it didn't assign a drive letter to either partitions.  Also it shows both partitions are 100% free space.  I put the drive back into the laptop, and it was able to boot, but failed loading screen.  I don't have the unit in front of me right now, so I can't tell you exactly what is the message.  The owner tried to do some kind of update on it, then it failed to boot.  So she tried to repair it using a repair cd, but that totally screw up her laptop.  Before the repair cd, she said she was able to see her files.  

I thought you can access Linux files from Windows.  I tried Explore2fs, but I guess in order to use it, the computer need to see the drive first(drive letter).  In this case, there is no drive letter for it. 

Any suggestion on how to retrieve the files from the drive?  I think I will burn a live cd, boot the laptop off it, and see if that works.

---

### Post by cadml on 2009-12-11
Try this, [http://www.ext2fsd.com/]("http://www.ext2fsd.com/") it will allow you to mount ext2/3 drives in windows.

---

### Post by fluffman86 on 2009-12-12
best option would be too boot your computer in Ubuntu and attempt to read the files that way, although I believe that running "repair" from a windows disk probably formatted the drive and erased everything.

---

### Post by t20t on 2009-12-12
The repair cd wasn't from windows, it was some kind of linux repair cd.  Anyone know why windows didn't assign a driver letter to the partition?  Could it because the partition wasn't in fat32 or ntfs?

---

### Post by airtonix on 2009-12-12
> **t20t said:**
> The repair cd wasn't from windows, it was some kind of linux repair cd.  Anyone know why windows didn't assign a driver letter to the partition?  Could it because the partition wasn't in fat32 or ntfs?

1 ) obtain ubuntu live cd
2 ) insert into cdrom drive on laptop
3 ) boot
4 ) see desktop
5 ) open file browser
6 ) press ctrl + l
7 ) type : computer://
8 ) see drives
9 ) ???
10 ) profit

---

