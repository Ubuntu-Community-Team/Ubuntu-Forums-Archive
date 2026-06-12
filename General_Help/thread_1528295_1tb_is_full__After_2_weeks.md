---
title: "1tb is full ? After 2 weeks?"
date: 2010-07-10
forum: General Help
---

### Post by imagxz on 2010-07-10
So I installed Ubuntu 10.04 on my main hard drive which is 1tb large and originally has 64x windows vista.

Now I'm being told that I have 89mb of space left on the file system. Can someone explain to me what is going on?\

- a noob

---

### Post by Steve603z on 2010-07-10
run the command ```
df -h
``` and paste the results

Also try going to Application > Accessories > Disk Usage Analyzer to find out if theres something has written a bunch of data to the hard drive.

It's possible that the installer did not properly partition your drive.

---

### Post by ice-brain on 2010-07-10
yes, the question is: have you installed ubuntu at your full hard drive?

---

### Post by imagxz on 2010-07-10
Filesystem            Size  Used Avail Use% Mounted on
/dev/loop0             24G   23G   86M 100% /
none                  2.0G  360K  2.0G   1% /dev
none                  2.0G  5.1M  2.0G   1% /dev/shm
none                  2.0G  216K  2.0G   1% /var/run
none                  2.0G     0  2.0G   0% /var/lock
none                  2.0G     0  2.0G   0% /lib/init/rw
/dev/sda1             932G  691G  242G  75% /host
/dev/sr0               48M   48M     0 100% /media/Setup
/dev/sdc1             466G  425G   42G  92% /media/MUSC & DATA
/dev/sde1             1.9G  359M  1.6G  19% /media/TANKWOMAN
/dev/sdb1             373G  293G   81G  79% /media/Data
/dev/sr3              644M  644M     0 100% /media/WD SmartWare
/dev/sdf1             466G  372G   94G  80% /media/TANKMAN_ONE



242 gigs should be available...

---

### Post by geirha on 2010-07-10
The virtual harddrive you installed ubuntu on is only 24 GiB, and you've used almost all of it, only 86MiB left. The windows filesystem you installed it in (/host), has 242GiB available...

You are probably using most of the space in your homedir. I suggest moving some files from your homedir to the filesystems you've got mounted in /media/

BTW, for future reference, it's a good idea to mention it's a wubi install. That may often make a difference on what solution to use.

---

### Post by imagxz on 2010-07-10
Ic ic. Thank you!

---

