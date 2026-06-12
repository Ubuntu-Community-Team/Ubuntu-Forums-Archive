---
title: "Merge Ubuntu Partition with Unallocated Space"
date: 2011-04-27
forum: General Help
---

### Post by Richiegs on 2011-04-27
My PC has two OS's -  Windows XP and Ubuntu - in a separate partition. There is some unallocated disk space between Windows and Ubuntu. I tried unsuccessfully to merge them together as one larger partition using Gparted in Ubuntu or another software in Windows. I thank you in advance for anyone who advises me hot to do it. Thanks again.

---

### Post by gandaran on 2011-04-27
> I tried unsuccessfully to merge them together as one larger partition using Gparted in Ubuntu 
use gparted only on the ubuntu live-cd.

---

### Post by Richiegs on 2011-04-27
> **gandaran said:**
> use gparted only on the ubuntu live-cd.

Did you mean to use Gparted within a Ubuntu Installation CD to merge two partitions together?

---

### Post by plucky on 2011-04-27
> **Richiegs said:**
> Did you mean to use Gparted within a Ubuntu Installation CD to merge two partitions together?

Yes.

Also if possible post a screenshot of the Gparted window to show us how the drive is partitioned.

---

### Post by AndyBoy_LV on 2011-04-27
You can also use a gParted live CD ([http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php))

---

### Post by techunit on 2011-04-27
Merging isn't the correct you need to expand your Ubuntu partition to fill the unallocated space not merge with it.

---

### Post by Mark Phelps on 2011-04-28
Without seeing your partition layout, I have to guess ...

But if you have an Extended partition, with your Ubuntu partitions inside of that, you have to resize the Extended partition first; then, you can resize the partition(s) inside of that.

Also, you can't resize your Linux partitions from inside Ubuntu because they have to be Mounted to run Ubuntu, and you can't work on Mounted partitions.  Which is why folks are telling you to do the work from a CD.

---

