---
title: "/home partition advice"
date: 2012-01-07
forum: General Help
---

### Post by alexanderbow on 2012-01-07
I'm terribly sorry to bring this thread back from the future, but I wanted to further understand the point of the home folder/partition in this type of situation. To my knowledge, the home partition contains the home folder which in turn contains typical data for storage. To me this means I would want the home partition somehow split/extended (im assuming this means raiding which im not enthused) or placed onto the storage HDD (if that's even possible). 

The deal is I have 1 30 gig primary (for hopefully /boot, swap, /root) and an 80 gig secondary (preferably for /home somehow). I'm thinking the 30's a smidge faster--for being IDE--and would be the perfect size: 100 Mb boot, 4 Gb swap, and 20 sumodd Gb root. Also, my home folder will contain a rather large virtual disk of WinXP; hence the need for a large /home partition. Any advice? Thanks all!

---

### Post by darkod on 2012-01-07
> **alexanderbow said:**
> I'm terribly sorry to bring this thread back from the future, but I wanted to further understand the point of the home folder/partition in this type of situation. To my knowledge, the home partition contains the home folder which in turn contains typical data for storage. To me this means I would want the home partition somehow split/extended (im assuming this means raiding which im not enthused) or placed onto the storage HDD (if that's even possible). 

The deal is I have 1 30 gig primary (for hopefully /boot, swap, /root) and an 80 gig secondary (preferably for /home somehow). I'm thinking the 30's a smidge faster--for being IDE--and would be the perfect size: 100 Mb boot, 4 Gb swap, and 20 sumodd Gb root. Any advice? Thanks all!

No need for separate /boot partition, create just the root and swap on the 30GB, and the /home on the 80GB.

Otherwise, related to the original question with 2 x 160GB disks, the only way to split partitions over two physical disks that I know of is LVM.

In your case the disks are 30 and 80 so it's probably not worth it. The role of LVM is that you create a Volume Group over as many physical devices as you want, and then create the partitions as Logical Volumes in that VG. If for example you buy a new disk in future, you add it to the VG and the new space is ready to be used. Without any reformatting or reinstalling.

---

### Post by alexanderbow on 2012-01-08
Hey thanks for the quick response darkod. i like the LVM idea; ill have to remember that for latter. it almost seems like a "virtual" RAID. if one of the HDD's crap out is all lost in the same manner as RAID?

Didnt realize the installer is normally supposed to see when there are two HDD's. ended up being a different problem: [http://ubuntuforums.org/showthread.php?t=1309128](http://ubuntuforums.org/showthread.php?t=1309128).

---

### Post by nothingspecial on 2012-01-08
Question moved to it's own thread.

> **alexanderbow said:**
> I'm terribly sorry to bring this thread back from the future, 

If you have a question, rather than posting on the end of an ancient thread, make a new one of your own.

Thank you.

---

