---
title: "FSTAB Problems"
date: 2009-07-18
forum: General Help
---

### Post by jfreak53 on 2009-07-18
Ok after reading many tutorials and everything I am still having problems with permissions on my ntfs partition when mounted.  When I don't have it mounted auto in the fstab and I mount it in gnome I can, using my admin user, not su, read-write and whatever on the drive.  But when I mount it on startup in fstab I cannot with my regular user.  Before mount using su I gave all permissions to the dir "disk" where it is mounted to my user, both group and user.  Then I put this in my fstab, and no go, I can not do anything to the drive with su.  How can I change this?

```
/dev/sda1       /media/disk     ntfs    nls=utf8,uid=1000,gid=1000,rw,exec,user,umask=0222 0    0
```

---

### Post by drs305 on 2009-07-18
The problem is with your umask of 0222. That effectively gives the user 555 permissions, which don't give you the access you want. Change the umask to 022 and you will be set, giving 755 permissions (or 0022 if you prefer).

---

### Post by jfreak53 on 2009-07-18
I knew it was something simple thanks.

---

