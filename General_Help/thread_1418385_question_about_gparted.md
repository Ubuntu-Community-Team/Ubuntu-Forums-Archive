---
title: "question about gparted"
date: 2010-02-28
forum: General Help
---

### Post by 8301 on 2010-02-28
when I formatted a 1 000 gig drive with gparted and ext4. I end up with 14 gig used space of what? There is a Lost and found folder with nothing in it. 

Is there a problem with ext4 file system? If I see the properties on the disk the 14 gig is ext3 Why?

---

### Post by geirha on 2010-02-28
It's reserved space, mainly used to avoid fragmentation. It is possible to reclaim it if you wish, but I recommend you keep it that way.

---

### Post by spiky001 on 2010-02-28
There was a topic posted on this the other day,the out come was that it was normal, trying to find thread

---

### Post by spiky001 on 2010-02-28
Have found this have a look

[http://forums.whirlpool.net.au/forum-replies-archive.cfm/1340874.html](http://forums.whirlpool.net.au/forum-replies-archive.cfm/1340874.html)

---

### Post by pirateghost on 2010-02-28
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

> **Modify Reserved Space  (Optional)**

 When  formatting the drive as ext2/ext3, 5% of the drive's total space is  reserved for the super-user (root) so that the operating system can  still write to the disk even if it is full. However, for disks that only  contain data, this is not necessary. 
NOTE: You  may run this command on a fat32 file system, but it will do nothing;  therefore, I highly recommend not running it. 
You can adjust the percentage of reserved space with the  "tune2fs" command, like this: 
 sudo tune2fs -m 1 /dev/sdb1This example reserves 1% of space - change this number  if you wish. 
[IMG]https://help.ubuntu.com/htdocs/ubuntunew/img/icon-info.png[/IMG] Using this command does not change  any existing data on the drive. You can use it on a drive which already  contains data. 

---

### Post by 8301 on 2010-02-28
Thanx

---

### Post by 8301 on 2010-02-28
> **8301 said:**
> Thanx

How do I mark this solved?

---

### Post by spiky001 on 2010-02-28
it,s in thread tools

---

