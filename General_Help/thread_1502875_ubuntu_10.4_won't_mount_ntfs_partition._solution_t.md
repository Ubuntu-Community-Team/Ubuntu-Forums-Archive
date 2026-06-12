---
title: "ubuntu 10.4 won't mount ntfs partition. solution too complex"
date: 2010-06-06
forum: General Help
---

### Post by c/Kr3t on 2010-06-06
i have an ntfs partition that i want to mount. before 10.4, all i had to do was add:

```


/dev/sdb2	/media/Share	ntfs-3g	user,auto,locale=en_US.utf8	0	0

```

to the fstab, and it would be mounted on startup, but now i can't do that. when i try to mount the partition, i get a window that says:

```

Unable to mount Share
Unprivileged user can not mount NTFS block devices using the external FUSE
library. Either mount the volume as root, or rebuild NTFS-3G with integrated
FUSE support and make it setuid root. Please see more information at
http://ntfs-3g.org/support.html#unprivileged

```

i don't understand what this means, and the guide that it recommends isn't very helpful to me either because i don't know what to do.

can anyone help me?

---

### Post by Leppie on 2010-06-06
try adding the user to the fuse group:
```
sudo adduser <username> fuse
```

also, the application ntfs-config takes away the pain of configuring the way the partition is mounted.

---

### Post by Morbius1 on 2010-06-06
Another way is to mount it the way Ubuntu would have mounted it had you instructed it to do so during your initial install of the OS. Ubuntu would have used UUID but it would have looked like this:

>  /dev/sdb2    /media/Share ntfs defaults,nls=utf8,umask=007,gid=46 0 0umask=007 will give owner and group read write access with no access to anyone else.
gid=46 represents group=plugdev. All local login users are members of the plugdev group so all local login users will have read / write access.

---

