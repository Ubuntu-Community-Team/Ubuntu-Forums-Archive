---
title: "Disk Partition Help"
date: 2011-05-10
forum: General Help
---

### Post by glamerboy on 2011-05-10
I am windows user and now switched to Ubuntu.. i have one question that.
my hard drive is 80 GB and i have partitioned it to 15 GB EXT and 2 GB swap and Remaining FAT32..
when i rebooted my system is mounted the fat32 drive space in following way:
My Computer> File System> Windows (Name Given to FAT32 Partition).
now my question is that i have my all data in Windows drive and will it be deleted if i change or reinstall my windows or it will behave independently.... HELP NEEDED....

---

### Post by PowerBarry43 on 2011-05-10
Hi, yes it will be deleted if you try to change the file system of your FAT32 to anything else all data will be lost. if you are doing a custom or clean install of windows you will also lose all of your files but if you do an upgrade you'll be able to keep them.

were you asking whether you'd lose your data on the EXT partition or the FAT32 partition?

Also in the future i would recommend using XFS and NTFS file systems as they are faster and more stable but there's no point changing your current installations as changing the file system would mean doing a complete reinstall of you O/S.
 
I hope that helped.

---

### Post by lithopsian on 2011-05-10
FAT32 works fine, don't worry about it.

If you want to reinstall Windows you could do it on a new partition and leave the old one alone with your data on it.  You would need to shrink the partition to make space, or use a different drive.

Ultimately you might want to copy the data you actually need to somewhere safe.  Either put it on a new partition and wipe the old one, or wipe everything except your important data from the FAT32 partition.  You only really need to keep it as FAT32 if you want to share the partition and data with another OS like Windows.

---

### Post by glamerboy on 2011-05-11
> **lithopsian said:**
> FAT32 works fine, don't worry about it.

If you want to reinstall Windows you could do it on a new partition and leave the old one alone with your data on it.  You would need to shrink the partition to make space, or use a different drive.

Ultimately you might want to copy the data you actually need to somewhere safe.  Either put it on a new partition and wipe the old one, or wipe everything except your important data from the FAT32 partition.  You only really need to keep it as FAT32 if you want to share the partition and data with another OS like Windows.

thanks buddy

---

