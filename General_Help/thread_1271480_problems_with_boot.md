---
title: "problems with boot"
date: 2009-09-20
forum: General Help
---

### Post by mcservies on 2009-09-20
it says 
gave up waiting for root device. Common problems:
-boot args(cat /proc/mdline)
-check rootdelay_ (did the system wait long enough)
check root= did the system wait fo the right device
-missing modules (cat /proc/modules: 1s /dv)
ALERT! /dev/disk/by-uuid/1820abe2-a5ef-4ea7-9db2-d84d37a119314 does not exist. 

Then it boots into a shell
v1.10.2 (ubuntu 1:1.10.2-2ubuntu7) built in shell ash



PLZ HELP!! 
it is greatly appreciated.

---

### Post by mcservies on 2009-09-20
All of this started after I updated it and it froze.

---

### Post by KiLaHuRtZ on 2009-09-21
When it drops to a root shell, cat '/boot/grub/menu.lst'...

```
cat /boot/grub/menu.lst
```

And also get the output of a list on '/dev/disk/by-uuid/'...

```
ls -l /dev/disk/by-uuid/
```

If you have separate partitions, you may have to mount them manually first...

```
mount /dev/hd[XY] /
mount /dev/hd[XY] /boot
mount /dev/hd[XY] /usr
mount /dev/hd[XY] /var
...etc...
```

Also, when you updated, what did you upgrade from and what did you upgrade to?

---

