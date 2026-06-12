---
title: "Partitioning problem."
date: 2011-05-08
forum: General Help
---

### Post by wbuntu on 2011-05-08
I used clonezilla to clone my old 20Gb harddrive to 80Gb.
after cloning i used gparted in xubuntu live cd to expand the partition to max space.
i booted with the new harddrive, And it was very strange:
```

$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1              18G   17G  923M  95% /
none                  744M  292K  744M   1% /dev
none                  750M     0  750M   0% /dev/shm
none                  750M  216K  750M   1% /var/run
none                  750M     0  750M   0% /var/lock
$ sudo mount /dev/sdb1 /media
[sudo] password for : 
$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1              18G   17G  844M  96% /
none                  744M  292K  744M   1% /dev
none                  750M  216K  750M   1% /dev/shm
none                  750M  220K  750M   1% /var/run
none                  750M     0  750M   0% /var/lock
/dev/sdb1              73G   17G   53G  24% /media

```

then ran gparted:[IMG]http://s4.postimage.org/9xlannhqh/image.gif[/IMG]very strange..
how can i fix that?
thanks

---

### Post by wbuntu on 2011-05-08
fdisk:
```

Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c7149

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9612    77201408   83  Linux
/dev/sdb2            9612        9726      921600    5  Extended
/dev/sdb5            9612        9726      920576   82  Linux swap / Solaris

```

---

