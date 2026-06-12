---
title: "Storage issue"
date: 2012-10-13
forum: General Help
---

### Post by X D face me on 2012-10-13
Hello everyone

my problem is that my file explorer says that there's only 1.5 gb free space. however, in windows, i've more than 100 gb of free space. i tried to enlarge my partition using gparted but gparted only shows the /dev/sda1 on host wich is the windows partition that uses the whole disk. does anyone know how to enlarge my linux partition? i'm using ubuntu 10.04 installed using wubi.

fdisk -l:
```
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfc2b36ae

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30402   244196352    7  HPFS/NTFS
```

df -h
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/loop0             17G   15G  1.2G  93% /
none                  998M  296K  998M   1% /dev
none                 1003M  1.6M 1001M   1% /dev/shm
none                 1003M  196K 1002M   1% /var/run
none                 1003M     0 1003M   0% /var/lock
none                 1003M     0 1003M   0% /lib/init/rw
/dev/sda1             233G  101G  133G  44% /host

```
X D face me

---

### Post by Wim Sturkenboom on 2012-10-13
I guess this is a wubi install and not a dual boot (so no other partitions). I don't know if it's possible to resize a wubi install (it's my impression that it's not possible).

You can post the output of
```

sudo fdisk -l

```
and
```

df -h

```
So somebody can verify.

---

### Post by X D face me on 2012-10-14
i've edited the first post. i believe the /dev/loop0 is the one i want to enlarge.

---

### Post by Wim Sturkenboom on 2012-10-14
Can't help you with wubi. You might be able to cleanup a bit

```

sudo apt-get clean

```

Try a search:
[resize wubi installed ubuntu](http://www.google.co.za/#hl=en&biw=1277&bih=1030&sclient=psy-ab&q=resize%20wubi%20installed%20ubuntu&oq=&gs_l=&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.&fp=ab0638e5779b7f69&bpcl=35277026&pf=p&pdl=300)

Just the friendly advise to make backups first (data in both windows and ubuntu) ;)

---

