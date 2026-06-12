---
title: "cannot find swap partition after hibernation"
date: 2010-02-23
forum: General Help
---

### Post by RavanH on 2010-02-23
Since I tested with suspending/hibernating my laptop, the system seems to have lost the swap partition. That is to say: it cannot find it at boot anymore. Some message shows during boot like "waiting for device listed in fstab: swap" or something and then it continues toboot normally. When I start the systemmonitor it reports Swap usage 0 byte out of 0 byte.

I checked my devices with ```
blkid
``` in terminal and it lists one of the partitions with its UUID as TYPE="swap".

Then I opened fstab with ```
sudo mousepad /etc/fstab
``` and noticed the line for the swap partition was using a completely different UUID. After changing the UUID to the correct (new) one and reactivatin swap with ```
sudo swapon -a
``` in terminal, all was well again but...

HOW could the UUID suddenly have changed?? Did that indeed have something to do with trying (and failing) Suspend and Hibernate ? If so, should I stay away from those features (that served me well under Windows) or is there something to be done about it ?

Thanks for any info :)

---

### Post by dcstar on 2010-02-24
> **RavanH said:**
> 
.......
HOW could the UUID suddenly have changed?? Did that indeed have something to do with trying (and failing) Suspend and Hibernate ? If so, should I stay away from those features (that served me well under Windows) or is there something to be done about it ?

Thanks for any info :)

The Swap UUID changes when people change the size of, or delete and recreate, the Swap partition.

---

### Post by plucky on 2010-02-24
Also make sure the UUID of ```
/etc/initramfs-tools/conf.d/resume
``` matches that of the swap partition.

Good Luck

---

### Post by RavanH on 2010-03-01
> **dcstar said:**
> The Swap UUID changes when people change the size of, or delete and recreate, the Swap partition.

Never did anything of the sort. Like i wrote, just tried suspend and hibernate and after that, swap had gone...

---

### Post by RavanH on 2010-03-01
> **plucky said:**
> Also make sure the UUID of ```
/etc/initramfs-tools/conf.d/resume
``` matches that of the swap partition.

Good Luck

Thanks! In that file, the old UUID was indeed still present. I suppose that would have made resume impossible? That is, if I would dare try Hibernation again ;)

---

