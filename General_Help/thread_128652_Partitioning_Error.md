---
title: "Partitioning Error"
date: 2006-02-12
forum: General Help
---

### Post by leach on 2006-02-12
I have 5 drives I'm trying to use LVM on, Two SCSI and Three IDE. I manually partition them all as physical lvm volumes and set configure them as one volume. I then automatically partition that volume, everything's fine but when I select the finish option I get the error- 

Error informing the kernel about modifications to partition
/dev/mapper/WMI-Banshee1 - Invalid Argument. This means Linux
Won’t know about any changes you made to
/dev/mapper/WMI-Banshee1 until you Reboot - so you shouldn't
mount it or use it in anyway before rebooting.
ERROR!!!

It gives me the options Ignore or Cancel but no matter what I select, it try’s to format the partitions and then tells me that It failed to and returns me to the partitioner.

If anyone knows of a solution any help would be appreciated.

---

### Post by jcl on 2006-02-12
Just a thought, what if you partition only your boot drive to work with LVM to get your system installed, then pull the other 4 drives in after your system is up and running and see if that works.

---

