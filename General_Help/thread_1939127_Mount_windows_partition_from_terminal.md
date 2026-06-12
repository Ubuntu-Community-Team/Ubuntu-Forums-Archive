---
title: "Mount windows partition from terminal?"
date: 2012-03-11
forum: General Help
---

### Post by miasmablk on 2012-03-11
i use clamav to run recursive scans on my windows partition from linux and would like to know how to mount my windows partition without the aid of nautilus..

output of sudo sfdisk -l:

```
Disk /dev/sda: 60801 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+     12-     13-    102400    7  HPFS/NTFS/exFAT
/dev/sda2         12+   5476-   5464-  43887027+   7  HPFS/NTFS/exFAT
/dev/sda3       5476+  60314-  54839- 440488960   83  Linux
/dev/sda4      60315+  60801-    487-   3904513    5  Extended
/dev/sda5      60315+  60801-    487-   3904512   82  Linux swap / Solaris

```

so i try to mount /dev/sda2 VIA

```
sudo mount /dev/sda2
```

and get: 

```
mount: can't find /dev/sda2 in /etc/fstab or /etc/mtab
```

however when i mount this partition through nautilus I get this:

```
mount: /dev/sda2 already mounted or /media/E6EE9E77EE9E3FAB busy
mount: according to mtab, /dev/sda2 is already mounted on /media/E6EE9E77EE9E3FAB
```


from here i run my scans VIA:

```
sudo clamscan -r  /media/E6EE9E77EE9E3FAB
```

---

### Post by linoseros on 2012-03-11
be sure that you've installed ntfs-3g package (do sudo apt-get install ntfs-3g) and when you want to mount a partition you need to specify at least 2 params the dev and the mount point.

So you need to create an empty folder let's say under /media/ :
sudo mkdir /media/mydisk

and then do :
sudo mount /dev/sda2 /media/mydisk

That's all ;)

---

### Post by miasmablk on 2012-03-11
hahaha thanks man.

---

