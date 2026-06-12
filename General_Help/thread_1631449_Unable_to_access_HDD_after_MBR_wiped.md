---
title: "Unable to access HDD after MBR wiped"
date: 2010-11-26
forum: General Help
---

### Post by Bob Fletcher on 2010-11-26
Wanted to restore laptop to Windows 7 and put Ubuntu on another machine.
The Laptop is an Acer and the Win 7 disks go into a propitiatory recovery screen. I have 3 choices reload Win 7 to new state, Load Win 7 and put everything in backup or Exit. 

I have loaded the Ubuntu 10:10 Live and downloaded ms-sys. The problem is Ubuntu is unable to mount the HDD - not in fstab.

I have Ubuntu and Win 7 on the HDD.

Can someone help me to get out of this mess.
Robert...

---

### Post by WorMzy on 2010-11-26
fstab is a file for automatically mounting filesystems, if the file systems aren't in there, it doesn't matter -- you can still mount the file systems manually.

What is the output of: ```
sudo fdisk -l
``` and ```
sudo blkid -c /dev/null
```?

---

### Post by wilee-nilee on 2010-11-26
That is a very confusing description thread starter.

---

### Post by Bob Fletcher on 2010-11-26
> **wilee-nilee said:**
> That is a very confusing description thread starter.

Sorry, I want to restore MBR for Windows I have wiped it.
ms-sys a linux ute that should be able to do this.

---

### Post by wilee-nilee on 2010-11-26
> **Bob Fletcher said:**
> Sorry, I want to restore MBR for Windows I have wiped it.
ms-sys a linux ute that should be able to do this.

lets have a look at the whole setup click on the bootscript in my signature and follow the directions to hava file generated with text in it. Come back to the thread with that text click on the [COLOR="Red"]#[/COLOR] in the reply panel and [COLOR="Red"][COLOR="Red"]paste all of the text text between the code tags.[/COLOR][/COLOR]

Do you have a install or recovery disc for MS. here is a recovery disc link for just this sort of situation. Needs to be burned as a image to a cd.
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

A install disc can be used as well just post that script first so we can see where your at.

---

### Post by Bob Fletcher on 2010-11-26
I ran fdisk and all I got was this
> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc12e36bb

   Device Boot      Start         End      Blocks   Id  System
ubuntu@ubuntu:~$ 

It looks like there is nothing there.

---

### Post by Bob Fletcher on 2010-11-26
Script results
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System



blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

```

---

### Post by WorMzy on 2010-11-26
> **Bob Fletcher said:**
> It looks like there is nothing there.

Indeed not, it looks like you destroyed the partition table. It might be possible to recover your partitions/data with recovery software, such as testdisk, anyfs-tools, ddrescue, and photorec. Never used any of them myself, but I'm sure you can find tutorials on these forums, or on google.

---

### Post by wilee-nilee on 2010-11-26
So did you have anything on the computer that can't be lost?

Do you have a install DVD for W7, acer will provide one or you can get the ISO from the original purchase probably, if it was a upgrade.

Was this a upgrade to W7 or was it installed when purchased?

---

### Post by Bob Fletcher on 2010-11-26
> **WorMzy said:**
> Indeed not, it looks like you destroyed the partition table. It might be possible to recover your partitions/data with recovery software, such as testdisk, anyfs-tools, ddrescue, and photorec. Never used any of them myself, but I'm sure you can find tutorials on these forums, or on google.

Thank you! I will go to bed now and just wait until the morning to give forum members  a chance to offer suggestions. My only consolation is I did a data backup today. Still a lot is still missing.

---

### Post by Bob Fletcher on 2010-11-26
> **wilee-nilee said:**
> So did you have anything on the computer that can't be lost?

Do you have a install DVD for W7, acer will provide one or you can get the ISO from the original purchase probably, if it was a upgrade.

Was this a upgrade to W7 or was it installed when purchased?

YES I have the recovery disks. but if this is as WorMzy has pointed out the partition table has gone I would like to get it back.

---

### Post by Quackers on 2010-11-26
testdisk has a real chance of recovering partitions in these cases. It is definitely worth a try.

---

