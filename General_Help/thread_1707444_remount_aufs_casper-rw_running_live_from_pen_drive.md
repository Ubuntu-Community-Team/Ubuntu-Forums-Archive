---
title: "remount aufs casper-rw running live from pen drive"
date: 2011-03-15
forum: General Help
---

### Post by maestrobwh1 on 2011-03-15
I have a flaky internal SD card reader that sometimes does not remount on wake from suspend.

I find if I am running the iso from the pen drive without persistence, I merely have to have a script in /etc/pm.sleep.d that has the device mounted at /isodevice to unmount then immediately remount to the same location.  Weird workaround but it does work.

However, when running live, it takes the partition casper-rw from the same SD card and mounts it at aufs, and t leaves my machine in a weird state where anything off the original iso works, but not from casper-rw.  

How do I remount /dev/sdc2 to aufs  at / (if need be) if it does not show up in the list?

df -h

aufs                  6.2G  2.6G  3.4G  43% /
none                  871M  320K  870M   1% /dev
/dev/sdc1             1.4G  1.3G   53M  97% /isodevice
/dev/loop0            1.3G  1.3G     0 100% /cdrom
/dev/loop1            1.2G  1.2G     0 100% /rofs
none                  878M  3.3M  874M   1% /dev/shm
tmpfs                 878M   73M  806M   9% /tmp
none                  878M  312K  877M   1% /var/run
none                  878M  4.0K  878M   1% /var/lock

---

