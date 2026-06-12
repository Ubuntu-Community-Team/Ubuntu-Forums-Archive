---
title: "USB will only mount read-only, even manually."
date: 2012-03-09
forum: General Help
---

### Post by Zephilinox on 2012-03-09
My usb is mounted automatically but with no permissions, so I do the following:

```

:~$ sudo umount /dev/sdd1

:~$ sudo mount -t ntfs /dev/sdd1 /media/USB -o rw,nosuid,nodev,uid=1000,gid=1000,dmask=0077,fmask=0177,uhelper=udisks

mount: warning: /media/USB seems to be mounted read-only.

```

how can I mount it without it being read-only? the rw option should have done that.

---

### Post by codemaniac on 2012-03-09
Hello mate  ,
Could'nt you simply mount it without setting up fmask , dmask options like simply below ?
```
sudo mount -t ntfs /dev/sdd1 /media/USB
```

---

### Post by codemaniac on 2012-03-09
Hello mate  ,
Could'nt you simply mount it without setting up fmask , dmask options like simply below ?
```
sudo mount -t ntfs /dev/sdd1 /media/USB
```

---

### Post by Zephilinox on 2012-03-09
> **codemaniac said:**
> Hello mate  ,
Could'nt you simply mount it without setting up fmask , dmask options like simply below ?
```
sudo mount -t ntfs /dev/sdd1 /media/USB
```

yes, I did try that initially, but I thought maybe I was leaving something important out of it so I did 'mount' and checked what options it had set to it when it gets mounted automatically, either way it is still read-only, I also tried setting umask=022 which seemed to work for someone but didn't for me.

and without those options, I have to sudo nautilus in order to read the drive.

---

### Post by Zephilinox on 2012-03-09
bump, any ideas?

---

