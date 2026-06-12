---
title: "how to resize lvm2 partitions?"
date: 2011-01-07
forum: General Help
---

### Post by rockager on 2011-01-07
i recently installed fedora on my system along with windows in a dual boot  unfortunately, the fedora partition is too big and is taking 80% of my disk space. lvm2 volumes are not recognised by windows so i decided to shrink my fedora lvm2 partition and create a new fat32 partition to store common data. i tried gparted from my ubuntu 10.04 CD but it was unable to resize the partition can someone suggest to me a GUI tool which could do the the resizing of an lvm2 partition?  thanks in advance.

---

### Post by psusi on 2011-01-07
I don't believe there is a gui tool that can do this.  First you probably need to shrink the logical volume with lvresize to free up space in the physical volume, then you can shrink the pv with pvresize.  Finally you can use fdisk to very carefully delete the partition and recreate it with the exact same starting sector, but shorter length ( not less than the size you reduced it to with pvresize ).

---

