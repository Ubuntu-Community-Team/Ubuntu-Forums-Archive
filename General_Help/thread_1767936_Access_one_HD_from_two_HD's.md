---
title: "Access one HD from two HD's"
date: 2011-05-26
forum: General Help
---

### Post by Blitz01 on 2011-05-26
Hi
Ive just installed Ubuntu alongside Windows 7, which was previously installed. What i am wondering  is there any way to access the hard drive that i saved all my stuff to on windows, in Ubuntu? It would be a bit of a waste if i couldn't. 

Thanks
Blitz01

---

### Post by sanguinoso on 2011-05-26
Which Ubuntu are you using? In Ubuntu 10.04 there is the places menu on the top bar, and when Ubuntu is installed alongside Windows it shows the other hard drive partitions under this places menu.

---

### Post by oldfred on 2011-05-26
As        sanguinoso says it should be in the left panel, but it will not say windows but usually something like 225GB or whatever size it may see it as.

Reading from the windows partition is not an issue. But writing too much into it or writing anything into it when hibernated in windows can cause major problems. Also the NTFS driver shows all files and folders including the system data that windows does not normally show. Do not accidentally move or delete critical system files. 

For the above reasons it is normally best to permanently mount the windows partition read only and create a read/write NTFS shared partition for any data you may want in both systems. Many windows only users suggest a separate data D: drive so when you have to reinsall windows you do not have to reinstall all your data (backups still required).

Easiest to permanently mount the NTFS:
Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
Above link was this post before:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions 
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)
mount [http://www.mjmwired.net/kernel/Documentation/filesystems/ntfs.txt](http://www.mjmwired.net/kernel/Documentation/filesystems/ntfs.txt)

---

