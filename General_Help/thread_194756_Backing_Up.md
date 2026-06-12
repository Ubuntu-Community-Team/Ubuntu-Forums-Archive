---
title: "Backing Up"
date: 2006-06-11
forum: General Help
---

### Post by cssutto on 2006-06-11
I am not getting anywhere with backing up.

I do not understand even rsync.

I would like to back up my Dapper complete to an external hard drive (Maxtor).  The Maxtor drive is partitioned with three partitions.

Any help would be appreciated.

CSSJR

df returns the following:

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda3              9614148   5356724   3769048  59% /
varrun                  387744       104    387640   1% /var/run
varlock                 387744         8    387736   1% /var/lock
udev                    387744       188    387556   1% /dev
devshm                  387744         0    387744   0% /dev/shm
lrm                     387744     18856    368888   5% /lib/modules/2.6.15-23-386/volatile
/dev/hda1             12284968   8898292   3386676  73% /media/hda1
/dev/hda2             23042876   6271896  16770980  28% /media/hda2
/dev/hda6             13473320    618256  12855064   5% /media/hda6
/dev/sdb1             22410640   6017296  16393344  27% /media/H:
/dev/sdb6             66332352  43237880  23094472  66% /media/Local Disk
/dev/sdb7             29492180    471204  29020976   2% /media/Local Disk-1

---

### Post by ????? on 2006-06-11
Is [this](http://www.psychocats.net/ubuntu/partimage.html) what you're looking for?

---

### Post by beercz on 2006-06-12
Have you tried rsnapshot?

[http://rsnapshot.org](http://rsnapshot.org)

---

