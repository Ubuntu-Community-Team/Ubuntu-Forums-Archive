---
title: "cant mount  dd .img backup of windows boot drive"
date: 2012-02-11
forum: General Help
---

### Post by ibod on 2012-02-11
Hi 

Can anyone help me with why I am getting this error and how to fix it.

```

$ sudo mount -o loop /media/fred/backup.img
mount: can't find /media/fred/backup.img in /etc/fstab or /etc/mtab

```

I can see the file

I am trying to mount a backup image file, made with dd of an ntfs windows drive 

I have made backups before and been able to mount them 
 
Thanks Ibod

---

### Post by Leppie on 2012-02-17
> **ibod said:**
> Hi 

Can anyone help me with why I am getting this error and how to fix it.

```

$ sudo mount -o loop /media/fred/backup.img
mount: can't find /media/fred/backup.img in /etc/fstab or /etc/mtab

```I can see the file

I am trying to mount a backup image file, made with dd of an ntfs windows drive 

I have made backups before and been able to mount them 
 
Thanks Ibod
you need to specify the mount point:
```
$ sudo mount -o loop /media/fred/backup.img /path/to/where/you/want/the/contents/to/appear
```

---

