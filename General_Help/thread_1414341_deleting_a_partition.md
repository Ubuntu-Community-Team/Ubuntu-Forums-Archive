---
title: "deleting a partition"
date: 2010-02-23
forum: General Help
---

### Post by sincerelyydavid on 2010-02-23
if i have ubuntu dual-booted with windows already, and wanted to get rid of windows entirely, how would i delete its partition?

---

### Post by Joe Ker1086 on 2010-02-23
post the output of 

```
sudo fdisk -l
```

---

### Post by tom4everitt on 2010-02-23
I would boot from a live cd and use gparted (its under applications->accessories). Its quite easy to figure it out.

---

### Post by Joe Ker1086 on 2010-02-23
> **tom4everitt said:**
> I would boot from a live cd and use gparted (its under applications->accessories). Its quite easy to figure it out.


No need to boot into a live cd if you have a working OS....plus if you are working from within ubuntu it would be harder to make a mistake and delete the ubuntu partition by mistake.

---

### Post by uncle-c on 2010-02-23
Very simple. If running on the Ubuntu use fdisk and follow the options. Just make sure you know on which device /partition holds your windows. 

[http://www.cyberciti.biz/faq/linux-how-to-delete-a-partition-with-fdisk-command/](http://www.cyberciti.biz/faq/linux-how-to-delete-a-partition-with-fdisk-command/)

Or just use or trusty old friend dd from a linux prompt ! 

Say that your Windows OS is on the /dev/sda2 partition then issue the following :

```

$ dd if=/dev/zero of=/dev/sda2 
```

It is not called "Disk Destroyer for nothing. You may have to be superuser to run this.

---

### Post by tom4everitt on 2010-02-23
> **Joe Ker1086 said:**
> No need to boot into a live cd if you have a working OS....plus if you are working from within ubuntu it would be harder to make a mistake and delete the ubuntu partition by mistake.

Oh, thats true. I just assumed that you couldn't modify anything on a hard drive with a mounted partition.

---

### Post by tom4everitt on 2010-02-23
> **uncle-c said:**
> Very simple. If running on the Ubuntu use fdisk and follow the options. Just make sure you know on which device /partition holds your windows. Or just use or trusty old friend dd from a linux prompt ! 

[http://www.cyberciti.biz/faq/linux-how-to-delete-a-partition-with-fdisk-command/](http://www.cyberciti.biz/faq/linux-how-to-delete-a-partition-with-fdisk-command/)

Say that your Windows OS is on the /dev/sda2 partition then issue the following :

```

$ dd if=/dev/zero of=/dev/sda2 
```

It is not called "Disk Destroyer for nothing. You may have to be superuser to run this.


This must be the most efficient, but also the most dangerous way to do it one could ever think of :)

---

### Post by Joe Ker1086 on 2010-02-23
> **tom4everitt said:**
> This must be the most efficient, but also the most dangerous way to do it one could ever think of :)

+1 yea, no room for error there lol.....it would definatly work though...

---

### Post by uncle-c on 2010-02-23
:P:P:P:P Quick, very gruesome and showing no remorse !

---

