---
title: "connect 2 hard disk of different manufacturer"
date: 2011-07-21
forum: General Help
---

### Post by alwaysonnet on 2011-07-21
Hello All,

I have seagate 40G IDE PATA hard-disk, 1.5G RAM and would like to extend another 40G hard-disk manufactured by Maxtor. I've Ubuntu 10.10 and Windows XP on different partitions.

will it be OK if i extend hard disks by different manufacturer and are there any risk of disk failure probably in the future.

please advice.

---

### Post by alwaysonnet on 2011-07-21
Hello All,

I have seagate 40G IDE PATA hard-disk, 1.5G RAM and would like to extend  another 40G hard-disk manufactured by Maxtor. I've Ubuntu 10.10 and  Windows XP on different partitions.

will it be OK if i extend hard disks by different manufacturer and are there any risk of disk failure probably in the future.

please advice.

---

### Post by An Sanct on 2011-07-21
As far as I can see, there should be no problems ... mixing HW manufacturers of hard disk drives is no problem, but if the specs say one is slower than the other, then a certain glitch will be present (only concerning the first time of read and access time ....) so freely use different types of disks, no harm can be done ;)

Linux uses a different partitioning system (I sound like an ///hole to myself for explaining this), so it is no problem to use multiple drives from different manufacturers :)

alwaysonnet ... a good thing to ask, tho :) I would like to say just, that Linux is an OS, that normally has support before anybody else (USB3 for example ...)

Edit: note ... support is here, always, if the hardware is not bound to a certain company (MS) or somehow bound in an other way (RIM) ... but most people do not need to worry about that...

---

### Post by Grenage on 2011-07-21
> **alwaysonnet said:**
> [FONT=Trebuchet MS]Hello All,

I have seagate 40G IDE PATA hard-disk, 1.5G RAM and would like to extend another 40G hard-disk manufactured by Maxtor. I've Ubuntu 10.10 and Windows XP on different partitions.

will it be OK if i extend hard disks by different manufacturer and are there any risk of disk failure probably in the future.

please advice.
[/FONT]

If by 'extend' you mean 'add' (not picking, just clarifying), then you should have no problems doing such.  Partition extension would require something like LVM, which I assume is not on the table.

---

### Post by howefield on 2011-07-21
Threads merged.

---

### Post by walt.smith1960 on 2011-07-21
I think you should be fine with 2 disks from different manufacturers.  These being PATA, be mindful of master/slave/CS(cable select) jumper settings. Also, you can only attach 2 PATA devices to one cable and many newer motherboards have only 1 PATA connector.  If you have a PATA CD drive, you may need to connect 3 devices and can only connect 2. This may not be an issue for you but something to be mindful of.

---

