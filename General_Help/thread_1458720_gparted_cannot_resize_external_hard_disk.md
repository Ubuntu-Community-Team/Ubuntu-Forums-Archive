---
title: "gparted cannot resize external hard disk"
date: 2010-04-20
forum: General Help
---

### Post by g.a. on 2010-04-20
Hi,

I have an external hard-disk with two partitions, a fat32 and an ext3.

I open gparted to resize the partitions but the only allowed operation is to check for information (see screenshot).

How can I manage it?

Thanks,
g.

---

### Post by indytim on 2010-04-20
Because the partitions are "mounted".  Note the little locked padlocks...

Try un mounting the partitions then accessing GParted -OR- boot to the LiveCD and run GParted from there.

IndyTim

---

### Post by g.a. on 2010-04-21
it worked. thanks.

it was not necessary to use a livecd, gparted perfectly recognized the external hard drive with unmounted partitions.

g.

---

