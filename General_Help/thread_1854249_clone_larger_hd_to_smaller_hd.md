---
title: "clone larger hd to smaller hd"
date: 2011-10-04
forum: General Help
---

### Post by xluke on 2011-10-04
Hello,
I'd like to migrate my OSes (Ubuntu 11.04 and Windows 7) from a hdd to ssd.  The hdd is 500gb and the ssd will be probably 120gb (still haven't chosen the purchase yet).  Is there an easy way to do this, perhaps using dd?  Used space is well below the size of the ssd, but they are split across multiple partitions as per a typical dual boot system.  

I appreciate any tips!

Thanks.

---

### Post by wildmanne39 on 2011-10-04
Hi, from what I have read on cloning, you have to have the same size or larger for the destination driver to be able to clone to it.
Thank you

---

### Post by papibe on 2011-10-04
As it is, no. But,..

You could resize your partitions using Gparted, so that they can fit on the new SSD. It should be very easy with the ext4/3 Ubuntu partitions.

As for Windows7, I would recommend booting into Windows itself, defraging a couple of times, and then using [Disk Management]("http://www.nirmaltv.com/2009/05/12/how-to-resize-disk-partition-in-windows-7/") reduce its partition. From experience, you may even need to repeat the process a couple of times since Windows7 kind of act 'greedy' when reducing its own partition.

Once the sums of the existing partitions fits into your SSD, you can use either [Clonezilla]("http://clonezilla.org/"), or Gparted from the Live Ubuntu CD or USB stick.

I hope that helps,
Regards.

---

