---
title: "ubuntu 9.10 cdrom stopped mounting?"
date: 2010-11-03
forum: General Help
---

### Post by LuniTux on 2010-11-03
Hello,

My cdrom has stopped auto mounting. I had a cd that was CD-RW and I wanted to erase the data on it. I followed the guide at: [http://www.ubuntugeek.com/ubuntu-tip-how-to-erase-cd-rwdvd-rw.html]("http://www.ubuntugeek.com/ubuntu-tip-how-to-erase-cd-rwdvd-rw.html")

and ran:

```
umount /dev/cdrom

cdrecord dev=/dev/cdrom blank=fast
```

After doing this, my cd drive stopped auto mounting.

Is there any way to fix this without reformatting my computer?

---

### Post by ajgreeny on 2010-11-03
If it has been blanked, there is no file system to mount, normal procedure.

Why do you want to mount it if there is nothing on it?

---

### Post by LuniTux on 2010-11-03
the problem is that I can no longer mount any cds not just the blank one. If I put in any cd (dvd, music, data, etc.) The cd does not mount

---

### Post by LuniTux on 2010-11-03
For what ever reason, The cd drive started working again

Thanks

---

