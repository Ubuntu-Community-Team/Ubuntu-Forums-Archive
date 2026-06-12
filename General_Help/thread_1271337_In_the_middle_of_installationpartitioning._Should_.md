---
title: "In the middle of installation/partitioning. Should I check the &quot;Format&quot;?"
date: 2009-09-20
forum: General Help
---

### Post by bridgetothesun on 2009-09-20
I'm in the middle of installing 9.04 on my PC. I have a 28gb extended partition that I have partitioned into two logical partitions of 8gb and 20gb size. The "/" goes into the 8gb and the "/home" goes into the 20gb. I've set both to Ext4 journaling but I'm not sure whether to check the "Format the partition" box. I have Windows 7 on another partition on my drive as well as a shared ntfs section of 75gb to share between Windows and Ubuntu.

Thanks.

---

### Post by blueridgedog on 2009-09-20
If it is unpartitioned space and/or new partitions, you have to format them.  Also, I would bump the 8g / to about 10 or 12.

---

### Post by drs305 on 2009-09-20
Yes, go ahead an format the partitions *if you are sure there is nothing you want on them*. If the are unformatted you must. You should format them if you are changing file system types (for instance ext3 to ext4) and otherwise formatting will ensure there is no 'clutter' on the partition as Ubuntu is installed.

---

### Post by bridgetothesun on 2009-09-20
They are new partitions. I used Gparted to make them from unallocated space on my drive. I first resized the Windows 7 partition to free up space and then made the NTFS, and Extended partitions. I'll bump the / up to 10gb, but I heard that the root partition doesn't need to be big since I have a big /home partition.

---

