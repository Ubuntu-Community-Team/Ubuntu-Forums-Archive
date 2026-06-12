---
title: "a query about filesystem storage..."
date: 2009-07-04
forum: General Help
---

### Post by tanixmukherzee on 2009-07-04
just now i installed jaunty...the disk usage analyzer shows me that the total filesystem capacity is 26.7 GB, used 3.5 GB,available 23.2 GB...but the window manager/file manager nautilus shows that i have free space of 19 GB...:confused: whats the reason for this contradiction,where's the 4.2 GB gone...can u people explain...whats the solution???

---

### Post by tommcd on 2009-07-04
Open a terminal (applications > accessories > terminal) and run:
```
df -h
```
The **df** command reports file system disk space usage. The **-h** option is for "human readable". This will list each of your partitions, as well as their used space and free space.
By default, about 5% of each partition is reserved space, so you don't fill up the partition and still have room for temp files, logs, and to administer the system. This is especially important for the root partition.

And welcome to the Ubuntu forums!

---

### Post by tanixmukherzee on 2009-07-04
> **tommcd said:**
> Open a terminal (applications > accessories > terminal) and run:
```
df -h
```The **df** command reports file system disk space usage. The **-h** option is for "human readable". This will list each of your partitions, as well as their used space and free space.
By default, about 5% of each partition is reserved space, so you don't fill up the partition and still have room for temp files, logs, and to administer the system. This is especially important for the root partition.

And welcome to the Ubuntu forums!

Thans for ur support bro...but i have done it before...and it shows....

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              23G  3.0G   19G  14% /
tmpfs                 497M     0  497M   0% /lib/init/rw
varrun                497M  108K  497M   1% /var/run
varlock               497M     0  497M   0% /var/lock
udev                  497M  144K  497M   1% /dev
tmpfs                 497M  652K  496M   1% /dev/shm
lrm                   497M  2.2M  495M   1% /lib/modules/2.6.28-13-generic/volatile
/dev/sdb1             3.9G  710M  3.2G  19% /media/2ND_GEAR

it shows the same result as was shown in nautilus stat bar...but my point is out of 23.2 GB taking away 4GB for temp files...logs...seems a bit strange to me...its not 5% but almost 20%...isnt it???

---

### Post by Elfy on 2009-07-04
It's likely that the disk usage analyzer, assuming you have it checking root is counting /dev/sdb1 3.9G 710M 3.2G 19% /media/2ND_GEAR. It would count that as it is mounted under /media

If I run it I get 250Gb when I only actually have 10Gb for /

Which would make the sums about right.

---

### Post by tanixmukherzee on 2009-07-04
oh yeah thats right...thanx bro...

---

