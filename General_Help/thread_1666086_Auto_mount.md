---
title: "Auto mount"
date: 2011-01-13
forum: General Help
---

### Post by L Style on 2011-01-13
how to set auto mount at startup. I have 3 partition how can i auto mount this partition at startup.

---

### Post by nomko on 2011-01-13
> **L Style said:**
> how to set auto mount at startup. I have 3 partition how can i auto mount this partition at startup.
 
Need some more information. Those 3 partition, are they on internal disc's? Or external disc's? And whats on those partition?

---

### Post by L Style on 2011-01-13
> **nomko said:**
> Need some more information. Those 3 partition, are they on internal disc's? Or external disc's? And whats on those partition?
their are may internal hard disk partitions in fat 32

---

### Post by vanadium on 2011-01-13
Hello, Nomko! (know him from another forum)

Indeed, removable drives (USB drives) do by default automount at startup. So I guess you have partitions on internal disk drives, and these by default are only mounted "on demand", i.e. when you click their icon in nautilus.

To have these automount as well, you need to edit the configuration file /etc/fstab, in order to "declare" these partitions there. In your /etc/fstab, your root partition and your swap have already been included by the Ubuntu installation program.

The otherwise excellent psycochocats provides a rather convoluted description here: [http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

Essentially, mounting a drive through /etc/fstab involves:

1) Creating a mount point, i.e., a directory where the file system of your partition will be "attached"
2) Adding a line in your /etc/fstab that contains six entries (1) the UUID of the partition (2) the mount point (3) the file system (4) the options (5) a number 0 (a remainder from the old days) and (6) another number indicating priority for checking. Make this 2 for data partitions.

(1) and (3) can be seen from the output of "sudo blkid". (2) is the directory (full path) you made yourself under 1) (4): If you do not have specific requirements, then put "defaults" there.

---

### Post by nomko on 2011-01-14
Check the following key is checked in Gconf-editor:
 
**> [B]/apps/nautilus/preferences/media_automount**[/B]
 
And there's also the key:
**>  [B]/apps/nautilus/preferences/media_automount_open**[/B]
 
This key can be unchecked if you don't want the (external) drives to be openend by nautilus automaticly

---

### Post by karthick87 on 2011-01-14
Install PYSDM,
```
sudo apt-get install pysdm
```

---

### Post by vanadium on 2011-01-14
Do not use pysdm. This software is somewhat outdated. It does not mount partitions by a unique identifier. Next problem you may get is that your partitions are not consistently mounted at the same mount point, or are not mounted at all.

---

### Post by sdibaja on 2011-05-24
> **vanadium said:**
> Hello, Nomko! (know him from another forum)

<<snip>>.

Essentially, mounting a drive through /etc/fstab involves:

1) Creating a mount point, i.e., a directory where the file system of your partition will be "attached"
2) Adding a line in your /etc/fstab that contains six entries (1) the UUID of the partition (2) the mount point (3) the file system (4) the options (5) a number 0 (a remainder from the old days) and (6) another number indicating priority for checking. Make this 2 for data partitions.

(1) and (3) can be seen from the output of "sudo blkid". (2) is the directory (full path) you made yourself under 1) (4): If you do not have specific requirements, then put "defaults" there.

Eureka! I finally got it! =D>

I got a device listing by running> sudo blkid -c /dev/null 
and then appended this to my fstab file, and it works!:
#
#----user input--- auto mount data drives 5/23/2011
#
#  Windows7
#/dev/sda1: LABEL="Windows7" UUID="4A5B809158A945C3" TYPE="ntfs"
UUID=4A5B809158A945C3 /media/Windows7 ntfs defaults 0 2
#
#  35GBFilesystem
#/dev/sda5: UUID="1852f2db-4099-40c2-a9cd-607c457b74ce" TYPE="ext4" 
UUID=1852f2db-4099-40c2-a9cd-607c457b74ce /media/35GBFilesystem ext4 defaults 0 2
#
#  data.docs
#/dev/sda6: LABEL="data.docs" UUID="1D11356F18CEC347" TYPE="ntfs"
UUID=1D11356F18CEC347 /media/data.docs ntfs defaults 0 2
#
#  S500back
#/dev/sdb1: LABEL="S500back" UUID="0282983E19313C6E" TYPE="ntfs" 
UUID=0282983E19313C6E /media/S500back ntfs defaults 0 2

Thanks! Peter
PS: [http://ubuntuforums.org/showthread.php?t=1726157](http://ubuntuforums.org/showthread.php?t=1726157) Post #4 was quite helpful too

---

