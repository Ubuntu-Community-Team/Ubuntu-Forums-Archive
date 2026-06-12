---
title: "how to mount another hard drive"
date: 2010-10-22
forum: General Help
---

### Post by miko5054 on 2010-10-22
id installed ubuntu 10.04 on 160GB hard drive 
and now i cant see the other hard drive 

only ubuntu installed ...

```
 Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000f04e9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18706   150250496   83  Linux
/dev/sda2           18706       19458     6037505    5  Extended
/dev/sda5           18706       19458     6037504   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2ae12ae0
 
```

thanks 
miki

---

### Post by .:PiXi²:. on 2010-10-22
What do you mean by "can't see the other hard drive"?
You can't see sdb?

---

### Post by miko5054 on 2010-10-22
i cant see it in gnome ,
i cant mount it and use it

---

### Post by .:PiXi²:. on 2010-10-22
Can you see it using gparted or palimpsest?

---

### Post by miko5054 on 2010-10-22
i can see it in  palimpsest

how i mount it ?

---

### Post by .:PiXi²:. on 2010-10-22
Select the drive in the left column, click on the partition in the graph of the disk and you should have an option under the graph that says "Mount Volume".
This isn't the most ideal method, do you want the partition mounted on startup?

---

### Post by miko5054 on 2010-10-22
yes i want it to mount on start up 
please

---

### Post by .:PiXi²:. on 2010-10-22
Is this the whole output of "sudo fdisk -l"?

```
 Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000f04e9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18706   150250496   83  Linux
/dev/sda2           18706       19458     6037505    5  Extended
/dev/sda5           18706       19458     6037504   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2ae12ae0
 
```

You should edit your fstab.
```

gksu gedit /etc/fstab

```
And add something like:
```

/dev/sdb1 /media/Disk ext4 defaults 0 0

```

---

### Post by miko5054 on 2010-10-22
i tried TO ADD 
```
/dev/sdb1 /media/Disk ext4 defaults 0 0 
```
but after restart start up couldn't found it

---

### Post by .:PiXi²:. on 2010-10-22
Post the complete output of sudo fdisk -l, /dev/sdb1 probably doesn't exist.

---

### Post by miko5054 on 2010-10-22
```
yair@yair-desktop:~$ sudo fdisk -l
[sudo] password for yair: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000f04e9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18706   150250496   83  Linux
/dev/sda2           18706       19458     6037505    5  Extended
/dev/sda5           18706       19458     6037504   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2ae12ae0

   Device Boot      Start         End      Blocks   Id  System
yair@yair-desktop:~$ 

```

---

### Post by miko5054 on 2010-10-22
```
yair@yair-desktop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000f04e9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18706   150250496   83  Linux
/dev/sda2           18706       19458     6037505    5  Extended
/dev/sda5           18706       19458     6037504   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2ae12ae0

   Device Boot      Start         End      Blocks   Id  System
yair@yair-desktop:~$ 

```

---

### Post by miko5054 on 2010-10-22
```
yair@yair-desktop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000f04e9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18706   150250496   83  Linux
/dev/sda2           18706       19458     6037505    5  Extended
/dev/sda5           18706       19458     6037504   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2ae12ae0

   Device Boot      Start         End      Blocks   Id  System

```

---

### Post by oldfred on 2010-10-22
Is this 500GB drive a new drive. It looks like it has no partitions. You do not mount a drive but mount the formated partitions that you have on a drive. 

Or did this drive have partitions that somehow disappeared?

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
[http://www.howtoplaza.com/how-to-install-ubuntu-904-on-a-manually-created-partition](http://www.howtoplaza.com/how-to-install-ubuntu-904-on-a-manually-created-partition)

---

### Post by schwabdale on 2010-10-22
Install PYSDM

---

