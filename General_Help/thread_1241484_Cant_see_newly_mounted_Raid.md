---
title: "Cant see newly mounted Raid"
date: 2009-08-16
forum: General Help
---

### Post by codeblue2k on 2009-08-16
So i added two identical drives to my Ubuntu machine for file storage. I was able to configure them in Raid0 and mount them. But for some reason I cant see the new drive in Computer. 

Here his my fdisk (The Disk /dev/md0 doesn't contain a valid partition table kind of worrys me)

```
codeblue@otm-srv:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004a98e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000de88a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdc: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x01550155

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9964    80035798+  83  Linux

Disk /dev/md0: 2000.4 GB, 2000404348928 bytes
2 heads, 4 sectors/track, 488379968 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table
codeblue@otm-srv:~$ 

```

And here is my cat /proc/mdstat

```
codeblue@otm-srv:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid0 sda1[0] sdb1[1]
      1953519872 blocks 64k chunks

```

```
codeblue@otm-srv:~$ df -k
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdc1             76904352   2270276  70727472   4% /
tmpfs                   513364         0    513364   0% /lib/init/rw
varrun                  513364       292    513072   1% /var/run
varlock                 513364         0    513364   0% /var/lock
udev                    513364       156    513208   1% /dev
tmpfs                   513364        84    513280   1% /dev/shm
lrm                     513364      2392    510972   1% /lib/modules/2.6.28-11-generic/volatile
/dev/md0             1922866224    200160 1824990072   1% /srv
codeblue@otm-srv:~$ 

```

Im brand new to Linux and Ubuntu, so any support you can give me would greatly be appreciated.

---

### Post by codeblue2k on 2009-08-16
Anyone??? Sorry to pester but I really need to get this server up and running before I leave tomorrow. I need to able to access the files on it while im gone. Please any help you can provide would be spectacular!

---

### Post by codeblue2k on 2009-08-16
bump

---

### Post by codeblue2k on 2009-08-16
please anyone... i leave for 2 weeks in less then 8 hours.

---

