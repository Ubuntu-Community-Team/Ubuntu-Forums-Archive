---
title: "fstab 'users' option not working"
date: 2012-09-05
forum: General Help
---

### Post by cheerPuncH on 2012-09-05
Hi,

I've scoured the internet with no luck, so here I am again. I need to mount a shared windows drive without using sudo. In fstab I've inserted the line...

```
//aib-fp01.aibiotech.com/share  /mnt/WindowsShared      cifs    umask=0000,noauto,user,user=user,password=pass,uid=500,gid=500     0       0
```

The umask,uid,and gid are all internet search attempts to get this line working without sudo. (It works with sudo.)

The error message I get is...
```
mount error(1): Operation not permitted
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
```

I've also tried users and got the same error. How can I get this working?

Thanks in advance!

Edit/Addon:

I also tried 
```
chmod 777 /mnt/WindowsShared
```
to make set writable permissions.

---

