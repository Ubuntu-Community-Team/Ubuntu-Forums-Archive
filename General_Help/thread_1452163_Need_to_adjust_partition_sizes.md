---
title: "Need to adjust partition sizes"
date: 2010-04-11
forum: General Help
---

### Post by drreed on 2010-04-11
This is my layout. I have 2 ubuntu's and a BSD on this box. (so I can mount these fs's from other places to work on them if necessary)

The one with a problem is Ubuntu 8.10, that boots from sdb1. As you can see, my root file system is 100%, and I have plenty of space available on sdb6 that I'd like to borrow.

What approach would you suggest?

I've looked at the partition editor and disn't see much help there.( I'm using kde3 btw.)

> root@bt:/# fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d92d0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          25      200781   83  Linux
/dev/sda2              26        9729    77947380    5  Extended
/dev/sda5              26         401     3020188+  82  Linux swap / Solaris
/dev/sda6             402        2381    15904318+  83  Linux
/dev/sda7            2382        9729    59022778+  83  Linux

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x90909090

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          25      200781   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sdb2              26        1531    12096945    5  Extended
Partition 2 does not end on cylinder boundary.
/dev/sdb3   *        1532        9730    65852986+  a5  FreeBSD
Partition 3 does not end on cylinder boundary.
/dev/sdb5              26         778     6048441   83  Linux
/dev/sdb6             779        1531     6048441   83  Linux
root@bt:/#
root@bt:/#
root@bt:/#
root@bt:/# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb5             5.7G  5.7G     0 100% /
tmpfs                1011M     0 1011M   0% /lib/init/rw
varrun               1011M   60K 1011M   1% /var/run
varlock              1011M     0 1011M   0% /var/lock
udev                 1011M  2.8M 1008M   1% /dev
tmpfs                1011M     0 1011M   0% /dev/shm
/dev/sdb1             190M   18M  163M  10% /boot
/dev/sdb6             5.7G  607M  4.8G  11% /root
overflow              1.0M   52K  972K   6% /tmp
root@bt:/#


---

### Post by colorlessprism on 2010-04-11
you should be able to resize the partitions using gparted. if you get/have a LiveCD and boot from it GParted should be on there. just make sure the hdd your working on is unmounted. this will take a LONG time. good luck

---

### Post by mistikkia on 2010-04-11
right ... so let me understand this ... you use the ubuntu install cd and where or when are you supposed to invoke gparted and how ?
because if i remember you can choose at some point during the installation process what filesystem top to put on your different partitions or to create others but I haven't seen how can you merge 2 partitions for example.

thank you in advance!

---

### Post by dptxp on 2010-04-11
I do not have Ubuntu on this machine but Gparted or some partition editor should be there in menu in administration.

No need for live cd unless you want to work on root partition.

---

### Post by drreed on 2010-04-11
> **mistikkia said:**
> right ... so let me understand this ... you use the ubuntu install cd and where or when are you supposed to invoke gparted and how ?
because if i remember you can choose at some point during the installation process what filesystem top to put on your different partitions or to create others but I haven't seen how can you merge 2 partitions for example.

thank you in advance!

Yep - and it worked like a charm, issue pwned!

LOL after I booted from the LiveCD, I realized the reason I couldn't resize those partitions was because I was running that OS, with the / mounted (of course). I also remembered that I'd cleverly partitioned everything just in case I did have to do this, and made sure the two partitions were adjoining.

I could have booted from 9.1 or BSD and run it from there. Oh well . . .

---

