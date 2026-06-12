---
title: "making non root own NTFS partitions"
date: 2006-04-07
forum: General Help
---

### Post by Gnowm on 2006-04-07
Hi yas, I have 2 NTFS partitions that are owned by root. Now I am aware that I cannot change these permissions (and yes i did do a recursive chown before i thought about it lol) but I am wondering if there is a way (for next time) at creation time, how i can give ownership to the normal user account.

Dont really wish to enable NTFS write as its not really a big deal to sudo to access them.

Cheers


--EDIT-- Just tried to mount it from a directory that user owns and that didn't work :(

---

### Post by amohanty on 2006-04-07
In your /etc/fstab

> /dev/sda1       /windows        ntfs    ro,user,auto,umask=022        0       0

of course replace the device and the mount point with the ones on your box, but I think that should do it.

the **user** and **umask** directives do the trick. Some info here:
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

HTH
AM

---

### Post by Gnowm on 2006-04-07
Thanks mate, i had in fstab 

```
/dev/hdb5       /media/hdb1/Win3 ntfs    nls=utf8,umask=0222 0 0
```

thank you  :+)

---

