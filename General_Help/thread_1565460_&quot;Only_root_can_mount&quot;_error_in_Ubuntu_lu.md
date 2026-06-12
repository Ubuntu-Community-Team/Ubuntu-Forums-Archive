---
title: "&quot;Only root can mount&quot; error in Ubuntu lucid"
date: 2010-08-31
forum: General Help
---

### Post by eternalthinker on 2010-08-31
Hi,
      I was trying to set the drives to auto-mount during boot in Ubuntu Lucid. For this I copy pasted the fstab entries which worked very well in Ubuntu Karmic. All partitions are ntfs ans all are in the format:

dev/sda1   /media/M$   vfat
defaults,user,exec,uid=1000,gid=100,umask=000    0   0
/dev/sda5   /media/stor   vfat
defaults,user,exec,uid=1000,gid=100,umask=000    0   0 

Even though the above uid, gid are used, the drives are mounted as root, and the normal user can access it in only read only mode. I changed the permissions to the mount folders to user. Even then the same error happens. 

Any solution?:(

---

