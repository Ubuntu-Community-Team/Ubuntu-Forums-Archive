---
title: "Ubuntu and SSD"
date: 2012-01-12
forum: General Help
---

### Post by -MVK- on 2012-01-12
Hello!
I am curious about the way Ubuntu manages SSD, even concerning low level operations in the file system. In particular, SSD are managed exactly in the same way of magnetic HD or they are managed differently to optimize the usage of each type of disk?
Thanks in advance!

---

### Post by oldfred on 2012-01-12
Standard installs have been modified to install on boundries that work better with SSD & 4k drives.

There are some settings and the newer kernels have some built in features. Most of the settings are related to reduced writes.

BIOS settings (SSD but also most systems)
[http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567561&viewfull=1#post567561](http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567561&viewfull=1#post567561)

You want journal to speed up system recovery if you have to do repairs or run fsck. But if partition is small then it does not take long to fsck anyway and without journal writing is reduced.
SSD’s, Journaling, and noatime/relatime 
[http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/](http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/)
noatime,nodiratime options in fstab to make the ssd last longer when using a ext4 partition

[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[https://wiki.ubuntu.com/MagicFab/SSDchecklist](https://wiki.ubuntu.com/MagicFab/SSDchecklist)
[https://help.ubuntu.com/community/UEFIBooting#Chainloading%20Windows%20x86_64%20UEFI-GPT](https://help.ubuntu.com/community/UEFIBooting#Chainloading%20Windows%20x86_64%20UEFI-GPT)

Some info is older and less and less special settings are required as systems are configured correctly. Some say the write life of a SSD is not really different than a hard drive so even some of the reduced write settings are not so critical (may be more important on flash drives as they are slow).

---

### Post by -MVK- on 2012-01-12
The second link doesn't work, but thank you very much for all the other ones! They are very interesting.

---

### Post by pqwoerituytrueiwoq on 2012-01-12
for the second link edit your fstab file
```
gksu gedit /etc/fstab
```
with ssd
```
UUID=a7bc74de-0ab3-48f8-a159-693f8bccb3cb /               ext4    discard,errors=remount-ro,noatime,nodiratime 0       1
```
without ssd
```
UUID=a7bc74de-0ab3-48f8-a159-693f8bccb3cb /               ext4    errors=remount-ro 0       1
```

---

