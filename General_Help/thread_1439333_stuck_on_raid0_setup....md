---
title: "stuck on raid0 setup..."
date: 2010-03-26
forum: General Help
---

### Post by husskii on 2010-03-26
Hi I just purchased a new server which came with 2x 750GB sata HDD's, It also have debian lenny installed and I would like to setup soft raid0 so they I can get the following partition layout..

Partition layout:
RAID 0 - / - 20 gig
RAID 0 - /home - the rest

can someone please show me how, Ive done some google searches and also looking in help guides, and I found a guide for mdadm, but having not done this before, I am getting lost..:shock:

my current config in webmin is 
```

/dev/md1 	Yes 	Mirrored (RAID1) 	5 GB 	/dev/sda1 | /dev/sdb1
/dev/md2 	Yes 	Mirrored (RAID1) 	693.13 GB 	/dev/sda2 | /dev/sdb2
```

or if I run the ```
dh -f
``` command in putty, I get this

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/md1              5.0G  669M  4.1G  14% /
tmpfs                 3.9G     0  3.9G   0% /lib/init/rw
udev                   10M  2.7M  7.4M  27% /dev
tmpfs                 3.9G     0  3.9G   0% /dev/shm
/dev/md2              688G  198M  653G   1% /home
```

Could really use the help...[-o<

Thanks 
Husskii

---

### Post by Tappy on 2010-06-14
This might help but it is raid 1
[http://www.howtoforge.com/how-to-set-up-software-raid1-on-a-running-lvm-system-incl-grub-configuration-debian-lenny](http://www.howtoforge.com/how-to-set-up-software-raid1-on-a-running-lvm-system-incl-grub-configuration-debian-lenny)

---

### Post by dcstar on 2010-06-15
> **husskii said:**
> Hi I just purchased a new server which came with 2x 750GB sata HDD's, It also have debian lenny installed and I would like to setup soft raid0 so they I can get the following partition layout..

Partition layout:
RAID 0 - / - 20 gig
RAID 0 - /home - the rest
.........

You are aware that "RAID 0" means that if **one** of your hard disks dies, you lose **all data** on **both** disks?

You are moving from 100% redundancy to anti-redundancy.

---

