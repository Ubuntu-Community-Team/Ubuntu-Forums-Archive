---
title: "Using Additional Hardrives"
date: 2006-04-13
forum: General Help
---

### Post by Sir_Penguin on 2006-04-13
I have just installed Ubuntu on my **DELL PowerEdge 1300/450** server (despite being a server it is intended for non-server uses). It has 4 SCSI hardrives but I only installed it onto one hardrive, about 8 GB, and used another 8 GB hardrive as a swap drive which the installer told me was reqiured. I also have two 35 GB hardrives which are blank (when Windows 2000 server was installed it said the hardrives have different amounts so I am rather confused, shown here is what Linux tells me I have). So what I would like to know is how to use the other two hardrives to store my data on. If you need any more information about my system or install just ask and I can post it back.
Finally, if this is in the wrong section, please could a mod move it.

---

### Post by justleen on 2006-04-13
the simplest way is to do a fdisk -l, to see if the drives picked up.
you should see them as something like /dev/sda to /sdd
If windows already complained about the sizes not matching, you might want to start with a fschk to check the disk. 
Once that done, you should be able to format the drives.
Assuming that this 3nd SCSI disk is /dev/sdc:
$sudo fdisk /dev/sdc and make a partition on it, e.g. /dev/sdc1
$sudo mkfs -t ext3 /dev/sdc1 to put a file system on it
 give it as mount point in /etc/fstab a sub-directory of /media/  eg. /media/drive1

---

