---
title: "Resizing root partion"
date: 2010-10-26
forum: General Help
---

### Post by leetkrew on 2010-10-26
i upgraded my hard disk from 120GB to 1TB. I cloned my old hard disk (dd if=/dev/sda of=/dev/sdb), checked the file system using live cd and managed to boot my new hard disk.

However, dd did not re-size my partition so i have 900GB of unused partition. My goal is to re-size my /dev/sda1 (mounted in /) and utilize my unused space.

Ubuntu Live CD did not allow me to re-size sda1.

please help,  thanks

---

### Post by lavinog on 2010-10-26
The Live CD will not let you resize sda partitions if it is using a swap partition on that drive.  You can swapoff with gparted (partition editor) first, then you should be able to resize the partition.

---

### Post by dcstar on 2010-10-27
> **leetkrew said:**
> i upgraded my hard disk from 120GB to 1TB. I cloned my old hard disk (dd if=/dev/sda of=/dev/sdb), checked the file system using live cd and managed to boot my new hard disk.

However, dd did not re-size my partition so i have 900GB of unused partition. My goal is to re-size my /dev/sda1 (mounted in /) and utilize my unused space.


There is really no need to resize the / partition just for the sake of it if you have so much space, however you should consider a separate /home partition (search for detailed instructions) and then maybe resize the / partition after you set that up.

---

### Post by leetkrew on 2010-10-27
thanks for the info. I am now just going to put my /home directory on other partition. It looks more nicer.

---

