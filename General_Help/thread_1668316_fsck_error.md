---
title: "fsck error"
date: 2011-01-16
forum: General Help
---

### Post by jpaulb on 2011-01-16
I tried to boot this morning the box crashed with warning
fsck.ext3: Unable to resolve 'UUID=7f7ffb3b-3a29-4521-8663-a6964d3fb54d'

What does this mean. how to I repair it.

---

### Post by Zill on 2011-01-16
jpaulb:  Were any other error messages given?

Please post the output of the following two commands:
```
cat /etc/fstab
```
```
sudo fdisk -l
```

---

### Post by jpaulb on 2011-01-18
multi posts

---

### Post by jpaulb on 2011-01-18
How do I delete instead of editing this?

---

### Post by jpaulb on 2011-01-18
> **Zill said:**
> jpaulb:  Were any other error messages given?

Please post the output of the following two commands:
```
cat /etc/fstab
```
```
sudo fdisk -l
```

I found the trouble by am at a loss as to how to fix it.I think I may have to get some help from the Debian forum since this is the only box left that is not running Ubuntu.

It all started when I ran into a brick wall trying to install Ubuntu server 8.04-1 on this box.

[http://ubuntuforums.org/showthread.php?t=876424](http://ubuntuforums.org/showthread.php?t=876424)
Where IDE & SATA caused problems with bootup

Fstab has the 2 IDE disk listed as /dev/hda & /dev/hdb, the updated fdisk lists them as /dev/sda & /dev/sdd.
The partition /dev/hda12 was never used so the other day I used Gparted to reformat it as an ext 4; I guess on the next boot up the problem started.


> 
jpb@maple:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda5       /               ext3    errors=remount-ro 0       1
UUID=7248e6bf-1056-4633-b76e-64b8e037ad6f       /               ext3    errors=remount-ro 0       1
# /dev/sda1       /backup         ext3    defaults        0       2
UUID=286272b6-19a0-4559-9179-a2655fbd1c6b       /backup         ext3    defaults        0       2
# /dev/hda1       /boot           ext3    defaults        0       2
UUID=acac46be-729f-477a-b3a6-877b6b2e006d       /boot           ext3    defaults        0       2
# /dev/hdb1       /home           ext3    defaults        0       2
UUID=d8fd667a-fc6f-4d5b-92ae-a1a9a48d574f       /home           ext3    defaults        0       2
# /dev/hda9       /opt            ext3    defaults        0       2
UUID=97d2be47-4804-466b-960e-9a71735869e2       /opt            ext3    defaults        0       2
#/dev/hda12      /spare         ext3    defaults        0       2
UUID=7f7ffb3b-3a29-4521-8663-a6964d3fb54d      /spare         ext3    defaults        0       2
# /dev/hda6       /tmp            ext3    defaults        0       2
UUID=6242c97a-f361-4e94-a51a-97ae5c86ee8e       /tmp            ext3    defaults        0       2
# /dev/hda7       /usr            ext3    defaults        0       2
UUID=9f9bbf00-b654-4867-aa71-9b48d7b9a663       /usr            ext3    defaults        0       2
# /dev/hda10      /usr/local      ext3    defaults        0       2
UUID=32e4e4de-d9da-4eb1-8980-80d50fa3353f      /usr/local      ext3    defaults        0       2
# /dev/hda11      /usr/share      ext3    defaults        0       2
UUID=b3f0bccf-a0ab-4183-b423-b5ea1057d984      /usr/share      ext3    defaults        0       2
# /dev/hda8       /var            ext3    defaults        0       2
UUID=f97bdb6a-695d-4d7a-a0b2-3f6fc8975731       /var            ext3    defaults        0       2
# /dev/hda2       none            swap    sw              0       0
UUID=df8fa7b7-38fb-42c1-b0b2-002c185f9fe9       none            swap    sw              0       0
# /dev/sdb1       /multimedia     ext3    defaults        0       2
UUID=4dd8e569-76de-4311-81ab-828da10a3d18       /multimedia     ext3    defaults        0       2
# /dev/sdb2       /temp		ext3    defaults        0       2
UUID=ef93127d-53d0-4a3f-9a71-6dc918022b92       /temp		ext3    defaults        0       2
# /dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/cdrom5        /media/cdrom0   udf,iso9660 user,noauto     0       0
192.168.0.122:/home	/mnt/traveller	nfs	defaults	0	0
192.168.0.121:/home	/mnt/j-Mini	nfs	defaults	0	0

jpb@maple:~$ 


maple:/home/jpb# fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00084387

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          12       96358+  83  Linux
/dev/sda2              13         255     1951897+  82  Linux swap / Solaris
/dev/sda3             256        9729    76099905    5  Extended
/dev/sda5             256         863     4883728+  83  Linux
/dev/sda6             864        1471     4883728+  83  Linux
/dev/sda7            1472        2079     4883728+  83  Linux
/dev/sda8            2080        3295     9767488+  83  Linux
/dev/sda9            3296        4511     9767488+  83  Linux
/dev/sda10           4512        5119     4883728+  83  Linux
/dev/sda11           5120        5756     5116671   83  Linux
/dev/sda12           5757        9729    31910912   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000401c8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       60801   488384001   83  Linux

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d390a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       60800   488375968+  83  Linux
/dev/sdd2           60801      121601   488384032+  83  Linux

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000dc420

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9729    78148161   83  Linux
maple:/home/jpb# 



---

### Post by Zill on 2011-01-18
> **jpaulb said:**
> ...Unable to resolve 'UUID=7f7ffb3b-3a29-4521-8663-a6964d3fb54d'...
> **jpaulb said:**
> ...Fstab has the 2 IDE disk listed as /dev/hda & /dev/hdb, the updated fdisk lists them as /dev/sda & /dev/sdd.
The partition /dev/hda12 was never used so the other day I used Gparted to reformat it as an ext 4; I guess on the next boot up the problem started...
Comparing your original post to the fstab it does seem that the errant UUID problem relates to /dev/hda12 /spare.
If /spare is not currently used then I would try commenting out this line in the fstab and rebooting.  If successful then the rest of the fstab must be OK.

You stated that /dev/hda12 is now formatted as ext4 but this still shows in the fstab as ext3.  Assuming the rest of the fstab is OK, I would try editing /dev/hda12 in the fstab from ext3 to ext4 to match the new format.

Otherwise, I would just replace the fstab file with the last working backup and see if that works OK, ensuring that /dev/hda12 is commented out.

I must admit that your fstab appears *very* complicated to me and I know my limitations ;-)  If you advise the outcome of my suggestions then I am sure someone more knowledgable will be able to assist further.

---

### Post by jpaulb on 2011-01-18
> **Zill said:**
> I would try commenting out this line in the fstab and rebooting.  If successful then the rest of the fstab must be OK.

I commented out the problem partition if fstab the system is running without the spare partition.

> **Zill said:**
> 
You stated that /dev/hda12 is now formatted as ext4 but this still shows in the fstab as ext3.  Assuming the rest of the fstab is OK, I would try editing /dev/hda12 in the fstab from ext3 to ext4 to match the new format.
I reformatted no change

> **Zill said:**
> 
I must admit that your fstab appears *very* complicated to me and I know my limitations ;-)  If you advise the outcome of my suggestions then I am sure someone more knowledgable will be able to assist further.
I got in trouble a few time a while back with everything in one big partition on a small hdd. One time I over looked the ¨delete downloaded package¨ in Synaptic the system finally ground to a halt. Another usr was one small partition which got filled with Docs and the system stopped.

Thanks for the help. I will probably upgrading the 2 ATA hdd to SATA since they were bought around 2005. One has a power on cycle of 3.6 years and the newer one of only 3.0

---

### Post by Zill on 2011-01-18
> **jpaulb said:**
> ...I reformatted no change...
Just to clarify my earlier comment... I *do* understand that you reformatted partition /dev/hda12 as ext4 using gparted.  However, your fstab still tries to load this partition as ext3 - this mismatch *may* be what is causing the problem when booting.

I suggest you will need to edit /etc/fstab and change ext3 to ext4, then reboot.  eg.
```
#/dev/hda12 /spare **ext3** defaults 0 2
UUID=7f7ffb3b-3a29-4521-8663-a6964d3fb54d /spare **ext3** defaults 0 2
```
change to
```
#/dev/hda12 /spare **ext4** defaults 0 2
UUID=7f7ffb3b-3a29-4521-8663-a6964d3fb54d /spare **ext4** defaults 0 2
```

---

### Post by jpaulb on 2011-01-18
[QUOTE=Zill;10372917]Just to clarify my earlier comment... I *do* understand that you reformatted partition /dev/hda12 as ext4 using gparted.  However, your fstab still tries to load this partition as ext3 - this mismatch *may* be what is causing the problem when booting.

Already did that.

As soon as I have a bit of spare time I am going to update my system

---

