---
title: "Mounting NTFS requires password on startup"
date: 2010-08-24
forum: General Help
---

### Post by jurco on 2010-08-24
Hi guys.

I have 3 NTFS partitions on second HDD which I marked to be mounted on startup. Thats fine but now I am asked for 3 admin pwd on startup (for each partition).

Is it possible to mount them automaticaly on startup without using admin pwd?

Thanks.

---

### Post by Morbius1 on 2010-08-24
> I have 3 NTFS partitions on second HDD which I marked to be mounted on startup.
I genuinely do not know what you mean by that statement. Marked to be started where? Did you set this up during the install or are you using some utility to do this?

Post the output of the following commands so we can find out what's going on:
```
sudo blkid -c /dev/null
```
```
cat /etc/fstab
```

---

