---
title: "Underscores in file names on CD"
date: 2009-07-09
forum: General Help
---

### Post by 0x656b694d on 2009-07-09
Hi,

I got several CDs burned under windows i guess, with Cyrillic file names.
Those names are shown with underscores, like this:
```

dr-xr-xr-x 1 root root    8192 2006-03-06 18:53 _____________________________
dr-xr-xr-x 1 root root    6144 2006-03-06 18:54 _______________________________
dr-xr-xr-x 1 root root    2048 2006-03-06 19:55 ______________________________2
dr-xr-xr-x 1 root root   10240 2006-03-06 18:55 ______________________________3
dr-xr-xr-x 1 root root    6144 2006-02-22 00:17 a_exler_rasskazy_storoza_muzeya
dr-xr-xr-x 1 root root    4096 2006-03-06 18:14 a_lebedev___den_surkova_01

```

This is what mount says:
```

/dev/sr0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=mikhail)

```

uname -a:
```

Linux mi7 2.6.31-2-generic #16-Ubuntu SMP Mon Jul 6 20:36:55 UTC 2009 x86_64 GNU/Linux

```

This is Karmic here with all recent updates.

I tried to remove utf-8 from /etc/fstab, and add iocharset=cp1251 (1251, windows-1251, koi8-r as well).

How do i mount such disks to get correct file names? (they look fine in windows)

Thanks!

-Mike

---

### Post by danwood76 on 2009-07-09
A quick search revealed this thread:
[http://ubuntuforums.org/showthread.php?t=610430](http://ubuntuforums.org/showthread.php?t=610430)

Unicode should read Cyrillic characters.
You may need to reboot for the changes to fstab to get noticed by hald also.

---

### Post by 0x656b694d on 2009-07-09
i bet i shouldn't need to reboot after changes to fstab.

i added iocharset=utf8 to fstab and got
```

$ mount | grep cdrom
/dev/sr0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,iocharset=utf8,user=mikhail)

```
but it didn't help. Other encoding options didn't work either.

thanks

---

