---
title: "Mount DVD only root can access"
date: 2011-01-30
forum: General Help
---

### Post by azenz on 2011-01-30
Having used Ubuntu for years, I continue to be amazed how this otherwise so sophisticated operating system can fail or confound in the most simple of things. Searching the internet and forums has not helped with this:

I installed Ubuntu Lucid 64 bit and found that my (internal) SATA DVD drive doesn't automount DVDs. But not only that, it only allows root access to DVDs!!! 

I tried this in fstab but to no avail:
/dev/sr0       /media/cdrom0   udf,iso9660 user,noauto,exec,umask=022 0       0

[I put the umask because previously 'mount' stated that umask was 0077, amazingly enough]

Permissions are as follows:
dr--r--r--  3 4294967295 4294967295   88 2011-01-30 14:24 cdrom0

Dolphin says: "access denied to /media/cdrom0". 

Your help would be GREATLY appreciated, because one would expect a modern operating system to give read access for DVDs to ALL USERS, and also to automatically automount them (or at least to easily enable automount). Thanks!

---

### Post by TeoBigusGeekus on 2011-01-30
Try this
```
sudo chmod 777 /media/cdrom0
```

---

