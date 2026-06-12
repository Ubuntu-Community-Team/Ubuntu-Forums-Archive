---
title: "There is not enough free space &quot;Cancel or Retry&quot;"
date: 2011-01-29
forum: General Help
---

### Post by Cheeze-It on 2011-01-29
Hey, everyone.

I was just copying files over to Ubuntu from my USB/Memory Stick Pro Duo, and apparently, I don't have enough space left to copy over files to the desktop/where ever. I had about 1 GB of hard drive left at that time,(on Windows) so I switched over back to Windows and deleted about 9GB worth of stuff. Back on Ubuntu, guessing that didn't work cause I still get the error.

I google searched this problem, but it wasn't any help. But I deleted some space from the Home Folder by viewing hidden files.(only about 35MB) I have a 110 GB C: Drive.

And here is the outcome of "df -h"
```
Filesystem            Size  Used Avail Use% Mounted on
/host/ubuntu/disks/root.disk
                      3.6G  3.5G  600K 100% /
tmpfs                 990M     0  990M   0% /lib/init/rw
varrun                990M  220K  989M   1% /var/run
varlock               990M     0  990M   0% /var/lock
udev                  990M  176K  989M   1% /dev
tmpfs                 990M  104K  989M   1% /dev/shm
/dev/sda2             103G   94G  8.1G  93% /host
lrm                   990M  2.5M  987M   1% /lib/modules/2.6.28-19-generic/volatile
/dev/sr1              6.7M  6.7M     0 100% /media/cdrom1
/dev/mmcblk0p1        3.7G  2.9G  864M  78% /media/disk
/dev/sdb1             7.5G  6.2G  1.4G  83% /media/PENDRIVE
/dev/sdc1             952M  939M   14M  99% /media/PSP 2000

```

---

### Post by oldos2er on 2011-01-29
3.6GB is pretty tight for an Ubuntu installation; you won't be able to install much additional software. There's some info here: [https://wiki.ubuntu.com/WubiGuide#How do I resize the virtual disks?](https://wiki.ubuntu.com/WubiGuide#How do I resize the virtual disks?) about resizing a Wubi install.

---

