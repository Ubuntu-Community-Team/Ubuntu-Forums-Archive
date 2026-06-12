---
title: "How do I mount my second HDD to my desktop"
date: 2010-01-14
forum: General Help
---

### Post by fogserver on 2010-01-14
Hello everybody, I'm pretty new to linux and i am trying to mount my second HDD to my desktop permanently so i don':(t have to mount it every time that i restart my computer can any body help me out PLEASE!!!!!!!!

---

### Post by ptviperz on 2010-01-14
Are you just wanting a shortcut to the hdd on your desktop?

You can do a df- h to list your drives/partitions

```
brent@brent-desktop:/media$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdc1              19G  4.3G   14G  25% /
udev                  4.0G  296K  4.0G   1% /dev
none                  4.0G  608K  4.0G   1% /dev/shm
none                  4.0G  116K  4.0G   1% /var/run
none                  4.0G     0  4.0G   0% /var/lock
none                  4.0G     0  4.0G   0% /lib/init/rw
/dev/sdc5             120G   48G   67G  42% /home
192.168.1.102:/share  917G  554G  363G  61% /media/PCH

```

Your second hard drive will probably be sdb (assuming sata drive)

Open a terminal (Applications->Accessorie->Terminal), cd to the Desktop folder (cd Desktop), then 

```
ln -s /dev/sbd1
```

That will give you a link to the drive. hope that's what you were asking :D

---

### Post by Morbius1 on 2010-01-14
Please post the output of the following commands:

Open **Terminal**
Type **sudo blkid -c /dev/null**
Type **cat /etc/fstab**
Type **mount**

And please identify which partition you would like to auto mount.

---

