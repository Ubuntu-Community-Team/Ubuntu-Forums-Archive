---
title: "Strange permissions FAT32 external HDD"
date: 2010-04-24
forum: General Help
---

### Post by audiodrumm on 2010-04-24
Hello, 

I'm having a strange issue with an external HDD formatted to FAT32.  

When I first started using the drive, I had no problems reading or writing to it.  However recently, I am unable to to write.  

I tried changing the permissions via  sudo nautilus->media->drive properties permissions, but this does not change anything.

When I try to access the drives via a non-root nautilus all of the folders are locked.  

I'm running Ubuntu 9.04.  Any help would be greatly appreciated.  Please let me know what other pieces of information you might need.  

Thanks a lot!

---

### Post by oldfred on 2010-04-24
It depends totally on how you mount it.

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)

---

