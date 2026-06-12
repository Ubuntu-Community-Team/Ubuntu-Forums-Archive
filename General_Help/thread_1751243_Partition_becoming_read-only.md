---
title: "Partition becoming read-only"
date: 2011-05-06
forum: General Help
---

### Post by lhcmacedo on 2011-05-06
So, the sda5 hard drive partition (named Luis Macedo) becomes read-only right after the system boots. I can't delete or download stuff on it anymore. On the permission tab everything is marked as "Create and Delete Files" but it actually doesn't do a thing.

Thanks!

---

### Post by oldfred on 2011-05-06
Welcome to the forums.

Are you mounting it with fstab or manually with Nautilus? What format is it? 

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions 
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

---

### Post by lhcmacedo on 2011-05-06
Ok, it's getting worse, the partition doesn't have a lock on it anymore, but you still can't write or delete anything in it. Also, the other partition, where Windows 7 is installed (you could write-read anything in it), doesn't show up anymore. These changes happened without reboot.

---

### Post by oldfred on 2011-05-06
It is usually better to only read from another system partition especially Windows. Better to have a shared NTFS for any data you want to have in both systems & set the windows system partition as read only except if you have to do repairs from Linux.:)

Did you just unmount the Win7 partition?

Post these:
```

sudo parted /dev/sda unit s print

df -H

```

---

