---
title: "Reallocating Partition not working"
date: 2010-12-05
forum: General Help
---

### Post by Rawgers on 2010-12-05
Well today I  successfully shrunk the Ubuntu partition on gparted (liveCD). But I am unable to add the unallocated space to my Windows 7 partition. Not sure what to do since the unallocated space can only be placed back in the Ubuntu partition.

Here is a SS of gparted
[IMG]http://img266.imageshack.us/img266/7642/snapshot1y.png[/IMG]

Thanks.

---

### Post by wannacme16 on 2010-12-05
Split it up and use one for Windows backup and the other for Ubuntu backups. Apart from rejoining it back to Ubuntu what else can you do?

---

### Post by dcstar on 2010-12-06
> **Rawgers said:**
> Well today I  successfully shrunk the Ubuntu partition on gparted (liveCD). But I am unable to add the unallocated space to my Windows 7 partition. Not sure what to do since the unallocated space can only be placed back in the Ubuntu partition.
........
Thanks.

Using a Live CD, unmount the Swap partition and then move the Ubuntu partition to the end of the Extended partition, then shrink the Extended partition.

You will then have free space to extend the Windows partition.

---

