---
title: "Need Help Removing Ubuntu from 2nd Hard Drive"
date: 2009-07-14
forum: General Help
---

### Post by crypticalz on 2009-07-14
Hi guys! I was wondering if anyone can help me out. I currently was testing out Ubuntu and I think its wonderful. The only problem is that I installed Ubuntu on my second HD (the whole hard drive...no partitions) . I didn't do any partitions and I really need some file storage from that drive for windows. I need to uninstall Ubuntu first and then create a partition and then install it back again. Can someone help me out I would appreciate it.

---

### Post by tommcd on 2009-07-15
There are 2 ways to do this:
1. Simply boot up XP and go to disk management, delete the linux partition(s) on the drive. Then use XPs disk management to make a NTFS partition of whatever size you want. Leave some space for Ubuntu. Then install Ubuntu to the space that is left over after creating the NTFS partition for Windows.

2. A better way to approach this is to get yourself a Parted Magic live CD:
[http://partedmagic.com/](http://partedmagic.com/)
Unzip the file in the terminal:
```

unzip pmagic-4.3.iso.zip

```
Check the md5sum of the iso that is created after you unzip it:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
Then just right-click on the **pmagic-4.3.iso** file (*not* the pmagic-4.3.iso.zip file) and choose "write to disk". Be sure to choose the slowest possible speed. Then check the md5sum of the CD you burned according to article I linked to above.

Boot the Parted Magic live CD and use it shrink the Ubuntu partition to whatever size you want. Leave the swap partition alone. Leave at least 10GB for Ubuntu if you can. More than 10GB is fine also. Ideally you should have a separate /home partition. But you can forget about that for now.
This will create "unallocated space" (i.e., free space) on the drive. 
Then boot up XP and create a NTFS partition for storage from the unallocated space using XPs disk management utility. Or you could create a NTFS partition using the Parted Magic live CD.

Method 2 avoids having to reinstall Ubuntu.

And welcome to the Ubuntu forums!

---

### Post by crypticalz on 2009-07-15
THANK YOU VERY MUCH FOR YOUR TIME! RESOLVED! 

thumbs up! 
cryptz

---

