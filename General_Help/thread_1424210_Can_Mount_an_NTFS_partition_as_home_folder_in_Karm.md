---
title: "Can Mount an NTFS partition as /home folder in Karmic"
date: 2010-03-07
forum: General Help
---

### Post by wdavro on 2010-03-07
I'm looking for a central location on my network of 1 Karmic and 3 XP Pros for my Documents, Videos, Music etc.  

I have an empty 1TB drive in my Karmic box currently formatted as one NTFS partition and I was thinking of mounting that drive in the Karmic /home folder.  

Will Karmic be all right using an NTFS partition as the /home folder?

---

### Post by ajgreeny on 2010-03-07
You can't use an ntfs partition as /home, but you can mount that partition anywhere you want in your linux filesystem and use it as a data storage partition.  All you will need to do is either use ntfs-config to mount it at boot time, or manually edit your /etc/fstab file to make it automount.

In order for the permissions to be as needed for /home, that partition or folder must be on one of the standard linux filesystems, usually ext3 or ext4 for ubuntu.  ntfs does not support linux permissions sufficiently for that to be so, and therefore can not be used.

---

### Post by dcstar on 2010-03-07
> **ajgreeny said:**
> 
.......
In order for the permissions to be as needed for /home, that partition or folder must be on one of the standard linux filesystems, usually ext3 or ext4 for ubuntu.  ntfs does not support linux permissions sufficiently for that to be so, and therefore can not be used.

You can (sort of) use NTFS mounts for the folders **under** the user's main folder in the /home tree for data storage - but you still compromise all Linux filesystem security.

NTFS cannot also be used for "hidden" Linux files/folders (names starting with a ".") - just try to use Gedit with the auto backups option enabled on a text file on a NTFS mount and see what happens.....  ;)

Bottom line: NTFS filesystems and Linux = Bad karma.

---

### Post by oldfred on 2010-03-07
No, you have to separate data from /home.

Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
Partitioning basics with some info on /data
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Share Windows partition:
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)

---

