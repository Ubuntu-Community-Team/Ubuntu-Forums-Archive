---
title: "How partitions are mounted: ro rw etc"
date: 2011-06-07
forum: General Help
---

### Post by rng on 2011-06-07
I have ntfs, fat32, ext3 and ext4 partitions on my computer. When I start ubuntu and open these partitions, some open without any problem, for others ubuntu asks password and for some it shows folders with a 'X' sign indicating I do not have permission to see these folders. So I want to know if there are any rules regarding how a partition will be mounted by ubuntu?

---

### Post by oldfred on 2011-06-08
It is different for Linux partitions as they support ownership and permission and the windows format partitions as they do not support ownership & permissions.

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
[http://www.mjmwired.net/kernel/Documentation/filesystems/ntfs.txt](http://www.mjmwired.net/kernel/Documentation/filesystems/ntfs.txt)
[http://www.mjmwired.net/kernel/Documentation/filesystems/vfat.txt](http://www.mjmwired.net/kernel/Documentation/filesystems/vfat.txt)

---

### Post by rng on 2011-06-08
Thanks oldfred for the links. I am going thru them.

---

