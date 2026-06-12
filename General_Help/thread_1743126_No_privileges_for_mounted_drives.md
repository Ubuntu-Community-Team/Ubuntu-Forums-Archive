---
title: "No privileges for mounted drives"
date: 2011-04-29
forum: General Help
---

### Post by EvilGnome on 2011-04-29
When I mount a drive to my computer (USB) it gives permission only to root. I have tried changing permissions using chown -R but this has not worked. I am not able to create folders on the drive or edit anything in any way. 

Is there a way for me to change the permissions or get into the folder as root?

---

### Post by oldfred on 2011-04-29
Is your external NTFS. It will show root but you have to set permissions & ownership with the mount. Wven if manually mounting it. The Nautilus default auto mount usually does not give much in the way of permissions.

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions 
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)
mount [http://www.mjmwired.net/kernel/Documentation/filesystems/ntfs.txt](http://www.mjmwired.net/kernel/Documentation/filesystems/ntfs.txt)
[http://www.mjmwired.net/kernel/Documentation/filesystems/vfat.txt](http://www.mjmwired.net/kernel/Documentation/filesystems/vfat.txt)

---

### Post by EvilGnome on 2011-04-29
The drive is formated as FAT32 so I didn't think I needed to worry about NTFS.

---

### Post by oldfred on 2011-04-29
Same rules for FAT. Only Linux based formats support Linux permissions & ownership.

---

