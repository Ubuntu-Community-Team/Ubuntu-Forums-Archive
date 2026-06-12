---
title: "problems mounting file system at boot"
date: 2009-11-18
forum: General Help
---

### Post by davidtuti on 2009-11-18
Hi,
Sometimes when I boot the filesystem "COMPLETADAS" doesnt mount it. In dolphin doesn't shows me and in a terminal I get:

```

ls -ltr

d????????? ? ?     ?         ?                ? COMPLETADAS

david@david:~/COMPLETADAS$ ls -tlr
ls: leyendo el directorio .: Error de entrada/salida
total 0
david@david:~/COMPLETADAS$

```

I have in the fstab
```

.............
..........
/dev/sdb5      /home/david/DESCARGAS  ntfs-3g
/dev/sdc1      /home/david/COMPLETADAS ntfs-3g
/dev/sda3      /home/david/auxiliar  ext3   defaults,user,auto 0 0

```

With Jaunty I dont have any problem, could you help me please?
Many thanks and sorry for my english!

---

### Post by Giblet5 on 2009-11-18
Try changing the fstab entries to complete entries. Examples:
```
/dev/sdb5      /home/david/DESCARGAS  ntfs-3g  rw,user,noatime,noexec,noauto,nls=utf8,umask=0666 0 0
/dev/sdc1      /home/david/COMPLETADAS ntfs-3g  rw,user,noatime,noexec,noauto,nls=utf8,umask=0666 0 0
/dev/sda3      /home/david/auxiliar  ext3   defaults,user,auto 0 0
```

Change the "noauto" entries to "auto" if you want these to mount at boot time.

Open a terminal window and check out the available options via ```
man mount
```

Cheers! (Mark it SOLVED if it is)

---

### Post by davidtuti on 2009-11-19
> **Giblet5 said:**
> Try changing the fstab entries to complete entries. Examples:
```
/dev/sdb5      /home/david/DESCARGAS  ntfs-3g  rw,user,noatime,noexec,noauto,nls=utf8,umask=0666 0 0
/dev/sdc1      /home/david/COMPLETADAS ntfs-3g  rw,user,noatime,noexec,noauto,nls=utf8,umask=0666 0 0
/dev/sda3      /home/david/auxiliar  ext3   defaults,user,auto 0 0
```

Change the "noauto" entries to "auto" if you want these to mount at boot time.

Open a terminal window and check out the available options via ```
man mount
```

Cheers! (Mark it SOLVED if it is)

Thanks! It seems that the ntfs filesystem is always mounted at boot but now I don't have permissions to write. I change your line by:

```

dev/sdc1      /home/david/COMPLETADAS ntfs-3g  rw,user,noatime,noexec,auto,nls=utf8,umask=0000 0 0

```

But I continue with the same problem :-(

Any help please?

---

### Post by Giblet5 on 2009-11-19
Are you very sure that the NTFS partition isn't corrupted?

Does it seem OK from Windows?

Do you have a language pack installed in Windows? Which one?

---

### Post by fluffman86 on 2009-11-19
> ls: leyendo el directorio .: Error de entrada/salida

I noticed this in the OP.  I'm not sure about what exactly the spanish means there, but it looks like a dying partition due to an I/O error.

---

