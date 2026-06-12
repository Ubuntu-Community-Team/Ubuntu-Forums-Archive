---
title: "Trying to recover partitioning"
date: 2011-03-27
forum: General Help
---

### Post by MaindotC on 2011-03-27
I was trying to allocate more space for my root partition but I accidentally clicked "cancel" while it was performing operations and things have been horrific since. I don't know if I can revert to the original state and of course I have not documented my steps.  The big problem I'm encountering is i'm receiving conflicting partioning information from various tools.  What I should have is a root partition about 15 GB, a home partition about 700 GB, a separate partition for porn about 150 GB, and two swap partitions.  But here's what I'm seeing:

From TestDisk:
```
Disk /dev/sda - 1000 GB / 931 GiB - CHS 121601 255 63
     Partition               Start        End    Size in sectors
* Linux                    0   1  1  1239 254 63   19920537
L Linux                 1240   1  1 62875 254 63  990182277
L Linux                62876   1  1 101045 254 63  613200987 [s]
L Linux                101046   1  1 120188 254 63  307532232
L Linux Swap           120189   1  1 121478 254 63   20723787
L Linux Swap           121479   1  1 121600 254 63    1959867
```

Gparted:
[IMG]http://img59.imageshack.us/img59/7316/62652028.png[/IMG]

And fdisk -l:
```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000dd281

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            1241      121601   966799702    f  W95 Ext'd (LBA)
/dev/sda2   *           1        1240     9960268+  83  Linux
/dev/sda5            1241       62876   495091138+  83  Linux
/dev/sda6          101047      120189   153766116   83  Linux
/dev/sda7          120190      121479    10361893+  82  Linux swap / Solaris
/dev/sda8          121480      121601      979933+  82  Linux swap / Solaris
/dev/sda9           62877      101046   306600493+  83  Linux
```

What is this "W95" business?

One thing I tried to fix this was to reinstall 10.04, listing /dev/sda2 as the root partition (couldn't find /dev/sda1):
[IMG]http://img190.imageshack.us/img190/1048/ss1ek.png[/IMG]
and I set /dev/sda2 as the root partition and format, and /dev/sda5 as the /home partition. When I tried to follow through with the install it wouldn't detect the existing account on the /home partition so I knew the jig was up.  Can anyone advise what I'm doing wrong or how I can get this back?  Testdisk will let me copy files from the /home partition so worst case scenario I can get another drive and copy the files but I'd just like to go back to the way it was if I can. Just wish I hadn't clicked "cancel"...one decision and things change in an instant...

---

### Post by dragonfly41 on 2011-03-27
RIPLinux on bootable CD or USB *might* be another useful tool to recover

[http://en.wikipedia.org/wiki/Recovery_Is_Possible](http://en.wikipedia.org/wiki/Recovery_Is_Possible)

[http://www.pendrivelinux.com/install-rip-linux-to-usb-from-windows/](http://www.pendrivelinux.com/install-rip-linux-to-usb-from-windows/)

---

### Post by MaindotC on 2011-03-29
Given the amount of help I've devoted to the forum, and the amount of information I've supplied, I was hoping for a little more assistance.

---

### Post by srs5694 on 2011-03-29
There's really not much help to give. When you clicked "cancel," you messed up whatever GParted was doing at that moment. The best thing to do is to back up what you can, create a fresh filesystem on that partition, and restore.

Oh, and "W95 Ext'd (LBA)" is just an extended partition. There are two types in common use, one of which originated with Windows 95, and hence is sometimes referred to as a "Windows 95" extended partition.

---

