---
title: "Lost /etc/fstab - Need to Rebuild"
date: 2011-12-01
forum: General Help
---

### Post by ks07 on 2011-12-01
Hey all,

Long story short, too much haste, not enough speed, tab completion and a typo means I'm now without an fstab. The machine this has affected is rather new and is using software raid, so I'd appreciate a few pointers on getting it fixed up. I've already made a start, but I'd rather not blindly test my attempt and leave myself with a non-booting OS. :P

Fstab rebuild attempt:
```
proc        /proc            proc    defaults                        0    0
none        /dev/pts        devpts    gid=5,mode=620                        0    0
/dev/md1    /            ext4    rw,relatime,errors=remount-ro,barrier=1,data=ordered    0    0
/dev/md2    /home            ext4    rw,relatime,barrier=1,data=ordered            0    0

```

/etc/mtab:
```
$ cat /etc/mtab 
rootfs / rootfs rw 0 0
/dev/root / ext4 rw,relatime,errors=remount-ro,barrier=1,data=ordered 0 0
none /proc proc rw,nosuid,nodev,noexec,relatime 0 0
none /sys sysfs rw,nosuid,nodev,noexec,relatime 0 0
none /proc/sys/fs/binfmt_misc binfmt_misc rw,nosuid,nodev,noexec,relatime 0 0
none /sys/fs/fuse/connections fusectl rw,relatime 0 0
/dev /dev devtmpfs rw,relatime,size=8183468k,nr_inodes=2045867,mode=755 0 0
none /dev/pts devpts rw,nosuid,noexec,relatime,gid=5,mode=620 0 0
none /dev/shm tmpfs rw,nosuid,nodev,relatime 0 0
none /var/run tmpfs rw,nosuid,relatime,mode=755 0 0
none /var/lock tmpfs rw,nosuid,nodev,noexec,relatime 0 0
/dev/md2 /home ext4 rw,relatime,barrier=1,data=ordered 0 0
```

fdisk:
```
$ sudo fdisk -l

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b5ce3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1306    10485760+  fd  Linux RAID autodetect
/dev/sda2            1306      243136  1942498304   fd  Linux RAID autodetect
/dev/sda3          243136      243201      525920   82  Linux swap / Solaris

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00095fa9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1306    10485760+  fd  Linux RAID autodetect
/dev/sdb2            1306      243136  1942498304   fd  Linux RAID autodetect
/dev/sdb3          243136      243201      525920   82  Linux swap / Solaris

Disk /dev/md2: 1989.1 GB, 1989118197760 bytes
2 heads, 4 sectors/track, 485624560 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md2 doesn't contain a valid partition table

Disk /dev/md1: 10.7 GB, 10737352704 bytes
2 heads, 4 sectors/track, 2621424 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md1 doesn't contain a valid partition table
```

df:
```
$ df -h
Filesystem            Size  Used Avail Use% Mounted on
rootfs                 10G  6.5G  3.0G  69% /
/dev/root              10G  6.5G  3.0G  69% /
/dev                  7.9G  176K  7.9G   1% /dev
none                  7.9G     0  7.9G   0% /dev/shm
none                  7.9G   76K  7.9G   1% /var/run
none                  7.9G     0  7.9G   0% /var/lock
/dev/md2              1.8T  271G  1.5T  16% /home
```

Thanks in advance, I'll try to be more careful next time ;)

---

### Post by crazy bird on 2011-12-01
Normally a backup file will be created. You could check the folder /etc/ for a file called fstab.bak. This is the backup file. See if you can replace the existing one with this one and hope that the .bak file is nof damaged. Compare the 2 files and check if the .bak file is correct. To swap the files:

- open a terminal
- type: **sudo rm /etc/fstab**
- type **sudo rename /etc/fstab.bak /etc/fstab**

What happens when you reboot?

---

### Post by ks07 on 2011-12-01
Sadly, no backup file present. Thanks for the suggestion.

(Not going to restart it just yet, it's a web server, trying to avoid as much downtime as possible!)

---

### Post by crazy bird on 2011-12-01
Maybe this will help you to repair your fstab file: [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab). 

And google: [http://www.google.nl/search?q=%22how+to+repair+fstab%22&hl=nl&num=10&lr=&ft=i&cr=&safe=images]("http://www.google.nl/search?q=%22how+to+repair+fstab%22&hl=nl&num=10&lr=&ft=i&cr=&safe=images")

---

### Post by ks07 on 2011-12-17
Managed to get hold of the iKVM to see the problem - turns out the main issue was a lack of /dev filesystem. Not needed on my desktop box, but absolutely necessary on this server, it would seem. The working fstab, if anyone is interested:

```
proc        /proc            proc        nodev,noexec,nosuid        0    0
/dev/md1    /            ext4        defaults,errors=remount-ro    0    1
/dev/md2    /home            ext4        defaults            0    2
/dev/sda3    none            swap        sw                0    0
/dev/sdb3    none            swap        sw                0    0
none         /dev             devtmpfs     rw,mode=0755             0     0
```

---

