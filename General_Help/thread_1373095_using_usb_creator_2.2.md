---
title: "using usb creator 2.2"
date: 2010-01-05
forum: General Help
---

### Post by pbj on 2010-01-05
i used the LiLi USB Creator 2.2 tool to create a bootable USB version of xubuntu 9.10. I chose 1 gig for persistent storage. The tool seemed to work, and I was able to boot into xubuntu from the USB key, and run a diskless workstation. But, I quickly ran out of disk space.

I was expecting my 1 gig of persistent storage to be on something called casper-rw. but, i cannot see that. it has been 20 years since I worked with unix, so I may be using the wrong commands. here is what "df" returns:

```
ubuntu@ubuntu:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
aufs                    537413    506777         0 100% /
udev                    962864       248    962616   1% /dev
/dev/sda1              1954036   1303104    650932  67% /cdrom
/dev/loop0              663040    663040         0 100% /rofs
none                    962864         0    962864   0% /dev/shm
tmpfs                   962864       120    962744   1% /tmp
none                    962864        92    962772   1% /var/run
none                    962864         0    962864   0% /var/lock
none                    962864         0    962864   0% /lib/init/rw
```why do I have a filesystem named "none"? udev looks like my 1 gig. should i just mount it and use it?

thanks for any help.

---

### Post by C.S.Cameron on 2010-01-05
You will not see casper-rw when booted from the drive. It will be visible if you plug the flash drive into an already running computer.

---

