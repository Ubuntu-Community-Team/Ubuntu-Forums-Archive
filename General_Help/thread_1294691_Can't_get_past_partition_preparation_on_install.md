---
title: "Can't get past partition preparation on install"
date: 2009-10-18
forum: General Help
---

### Post by denizente on 2009-10-18
Hi,
 
I'm trying to install Ubuntu as the only OS on a machine that currently has Vista on it. Vista wasn't registered within the 1 month period they specify & consequently the machine won't connect to the net. When I went thru' the Ubuntu install it wouldn't prepare the partitions - the forward & back buttons just took me to the same screen each time & nothing happened - couldn't get past that stage. Tried looking at the partitions with GParted but no partition data was showing at all!! Any advice welcome...

---

### Post by jward3010 on 2009-10-18
Can installer appear to make partitions?

---

### Post by mike555 on 2009-10-18
Are you trying to partition or just install? if just install then let it use the whole HD and it will make a swap partition for you ............. 


if your trying to partition you might try a newer gparted from the "Parted Magic" cd ...

---

### Post by jward3010 on 2009-10-19
Have you a particularly strange setup with RAID cards or ATA cards etc.? GParted should show in it's top right corner the device name of the drive you're looking at, if nothing is there then it hasn't detected your drive (highly unlikely) or you're drive has become dislodged.

---

