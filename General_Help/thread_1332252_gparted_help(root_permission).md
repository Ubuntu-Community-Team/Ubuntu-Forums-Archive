---
title: "gparted help(root permission)"
date: 2009-11-20
forum: General Help
---

### Post by muscularsage on 2009-11-20
hi i used gparted software and resized a partition in ma hard disk and split it into two partitions.now am not able to copy or paste files in those partitions.it shows the owner as root.am not able to do any thing in this partition. kindly help.

---

### Post by meindian523 on 2009-11-20
Did you format the partitions? What filesystem? Where are you trying to copy from? If the partitions were created correctly, they should appear in the Places menu, and you should be able to mount them, thence copy, move, etc as you wish.

---

### Post by ajgreeny on 2009-11-20
The permissions will be related to the owner and permissions set for the mount point folder.  They can be changed easily, but we need to know the current situation, so can you post the output of ```
cat /etc/fstab
ls -l /media
sudo fdisk -l
```one line at a time, and it should be possible to sort you out.

---

### Post by warfacegod on 2009-11-20
Try this, it worked for me.

sudo chown -R username:username /media/drivename

---

### Post by meindian523 on 2009-11-20
That would indeed work, provided OP can mount his partitions.

---

### Post by warfacegod on 2009-11-20
> **meindian523 said:**
> That would indeed work, provided OP can mount his partitions.

Why would mounting be needed? As long as the computer "sees" the hardware it should still work.

---

### Post by warfacegod on 2009-11-20
I just answered my own question. If the drive isn't mounted, it won't show in the media folder. Duh!

---

### Post by muscularsage on 2009-11-21
ajay@ajay-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=d09b915c-60e6-4854-a17f-10fa9d9a9cdd /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=4ad9543a-bd42-4a9d-9d7c-16f6c63e1c99 none            swap    sw              0       0
# swap was on /dev/sda7 during installation
UUID=d00724ce-3f82-4239-ac7c-8031ebb31e73 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by muscularsage on 2009-11-21
ajay@ajay-laptop:~$ ls -l /media
total 8
drwxr-xr-x 21 root root 4096 2009-11-20 15:35 7db0c0ba-e10f-4c92-ad30-0a750a4ba08c
lrwxrwxrwx  1 root root    6 2009-11-05 01:06 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2009-11-05 01:06 cdrom0
ajay@ajay-laptop:~$

---

### Post by muscularsage on 2009-11-21
ajay@ajay-laptop:~$ sudo fdisk -l
[sudo] password for ajay: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69205244

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        6577    52829721   83  Linux
/dev/sda2           25638       38913   106639470    5  Extended
/dev/sda3            6578       25637   153099450   83  Linux
/dev/sda4          167628      167631       25817+   0  Empty
Partition 4 does not end on cylinder boundary.
/dev/sda5           38188       38913     5831563+  82  Linux swap / Solaris
/dev/sda6   *       25638       37671    96663042   83  Linux
/dev/sda7           37672       38187     4144738+  82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by muscularsage on 2009-11-21
i mean ive created an ext4 partition it shows in tthe places as well am able to mount but it des not show me as the owner in properties menu.....it shows that am not the root.....

---

### Post by muscularsage on 2009-11-21
@warfacegod man it worked gr8! thanks 4 ur help!

---

### Post by jacobs444 on 2009-11-21
sudo chown username:username /whereveryoumountthedrive

---

