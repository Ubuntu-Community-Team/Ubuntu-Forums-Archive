---
title: "Increase / root partition size"
date: 2012-09-08
forum: General Help
---

### Post by jaz010 on 2012-09-08
Hello I have an Ubuntu virtual machine running OpenErp, I ran out of space on / root.
Below the output of df 


# df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/mapper/OpenERP-root
                       3326104   3113052     44092  99% /
udev                   1019140         4   1019136   1% /dev
tmpfs                   411288       372    410916   1% /run
none                      5120         0      5120   0% /run/lock
none                   1028212         0   1028212   0% /run/shm
/dev/sda1               233191     23964    196786  11% /boot

I instaled an new virtual disk with a size of 8GB


root@OpenERP:/var/log/postgresql# lshw -short -c disk
PCI (sysfs)

H/W path             Device      Class      Description
=======================================================
/0/100/7.1/0.0.0     /dev/cdrom  disk       SCSI CD-ROM
/0/100/10/0.0.0      /dev/sda    disk       4294MB SCSI Disk
/0/100/10/0.1.0      /dev/sdb    disk       8589MB SCSI Disk


Can Anyone help me how to mount use this disk to extend / partition.

Thank you in advance.

---

### Post by dcstar on 2012-09-08
> **jaz010 said:**
> Hello I have an Ubuntu virtual machine running OpenErp, I ran out of space on / root.
.........
Can Anyone help me how to mount use this disk to extend / partition.

Thank you in advance.

Pointless, just read some of the hundreds of detailed posts already in the forum on extending partitions.

---

### Post by oldfred on 2012-09-08
I do not know lvm, but most posts are on using gparted.

[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)

[http://tldp.org/HOWTO/LVM-HOWTO/commontask.html](http://tldp.org/HOWTO/LVM-HOWTO/commontask.html)

---

