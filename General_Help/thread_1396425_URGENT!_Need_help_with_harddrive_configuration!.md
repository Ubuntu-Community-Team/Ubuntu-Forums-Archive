---
title: "URGENT! Need help with harddrive configuration!"
date: 2010-02-02
forum: General Help
---

### Post by artheus on 2010-02-02
On login I get this message

```

Linux www9 2.6.31-16-server #53-Ubuntu SMP Tue Dec 8 05:08:02 UTC 2009 x86_64

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/

  System information as of Tue Feb  2 08:43:48 CET 2010

  System load:      0.01              Memory usage: 9%   Processes:       132
  Usage of /export: 29.5% of 1.30TB   Swap usage:   0%   Users logged in: 1

  **=> / is using 99.8% of 19.22GB**

  Graph this data and manage this system at https://landscape.canonical.com/

Last login: Tue Feb  2 08:38:24 2010

```

And because of the 99.8% usage of 19.22GB the mysql server won't start. And it is really Urgent that it does.

It's my companies server, there was a tech guy here who messed up the server big-time, before I started here.

The "fdisk -l" command makes this output

```
Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000cfcab

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      104391   83  Linux
/dev/sda2              14       91201   732467610   fd  Linux raid autodetect

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007f22e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       91188   732467578+  fd  Linux raid autodetect
/dev/sdb2           91189       91201      104422+  83  Linux

Disk /dev/sdc: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000433f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       91188   732467578+  fd  Linux raid autodetect
/dev/sdc2           91189       91201      104422+  83  Linux

Disk /dev/md0: 1500.1 GB, 1500093349888 bytes
2 heads, 4 sectors/track, 366233728 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe8900690

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      121601   976760001    c  W95 FAT32 (LBA)
```

And here is the content of the /etc/fstab

```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/VolGroup00-LogVol00 /               ext4    errors=remount-ro 0       1
/dev/mapper/VolGroup00-LogVol01 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/mapper/VolGroup00-LogVol02 /export         ext3    defaults        0       2
UUID=58545997-98ad-480f-abd7-a18210e14157       /backup         ext4    defaults        0       1
```


I don't really get where that 19.22GB comes from. And I've tried to start the server up with a LiveCD and making this bigger with GParted. But I can only find one 100 mb partition on each one of the 750 GB HDD's. And what I find is that I can not configure the LVM Raid with GParted.

Please! What can I do to fix this? Without loosing data, and fixing this in as little time as possible.

//Artheus

---

### Post by ImperialXT on 2010-02-02
if you can get in, couldn't you just find the source of the large files  in that partition and move them to /export I'd suggest looking into the users /home dirs

---

### Post by artheus on 2010-02-02
Well.. Sorrily the home folder is already in /export
and the /home is a link to /export/home

```
  3060 lrwxrwxrwx   1 root   root     12 2009-12-08 14:25 home -> /export/home
```


But I will move other stuff that is big from / to /export..

Thanks.

---

