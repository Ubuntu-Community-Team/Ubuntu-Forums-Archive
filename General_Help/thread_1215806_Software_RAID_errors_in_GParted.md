---
title: "Software RAID errors in GParted"
date: 2009-07-17
forum: General Help
---

### Post by I Use Dial on 2009-07-17
I have a fresh install of Ubuntu 8.04 on a 60 GB PATA drive and I have two identical SATA 1 TB unused drives that I want to install a type 1 RAID on.

Following these [instructions]("https://wiki.ubuntu.com/Raid") on the wiki, I ran the following:

> $ cd /
$ sudo -s -H
# mdadm /dev/md0 --create --auto yes -l 1 -n 2 /dev/hdc /dev/hdd

Then I ran:

> # mk.xfs /dev/md0
# mkdir /media/teraraid
# cat >> /etc/fstab
     /dev/md0        /media/teraraid           xfs    defaults   0       0
     ^D
# sudo chown -R USERNAME:USERNAME /media/teraraid

I just looked at the volume in GParted and it has an exclamation mark and the following message when I right click and select Information:

> [I]/dev/md0p1: No such file or directory

fatal error -- couldn't initialize XFS library

/dev/md0p1: No such file or directory

fatal error -- couldn't initialize XFS library

Unable to read the contents of this filesystem!
Because of this some operations may be unavailable.[/I]

This is the first time I've set up a RAID before.

Should I be concerned??

---

### Post by fjgaude on 2009-07-21
Well, gparted doesn't understand raid. So you likely have everything working without knowing it.

What does this show:

```
sudo mdadm /dev/md0
```

Thanks!

---

### Post by I Use Dial on 2009-07-22
/dev/md0: 931.51GiB raid1 2 devices, 0 spares. Use mdadm --detail for more detail.

---

