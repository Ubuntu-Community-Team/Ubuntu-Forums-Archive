---
title: "NTFS not mounting anymore"
date: 2010-05-15
forum: General Help
---

### Post by SINZAR on 2010-05-15
My second hard drive is no longer mounting in 10.04. This is a fresh install on a dual boot system. The drive mounted fine the last few times I tried to access it and now I get the error:

"Error mounting: mount exited with exit code 12: Failed to read last sector (625134601): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/sdb2': Invalid argument
The device '/dev/sdb2' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?"

From command line I get:
sudo mount -t ntfs /dev/sdb /home/ben/E-drive/
NTFS signature is missing.
Failed to mount '/dev/sdb': Invalid argument
The device '/dev/sdb' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

I ran checkdisk on it from Windows and it came up clean. My other drives/partitions are mounting fine with the exception of this one. 

Any ideas?

---

### Post by Ozymandias_117 on 2010-05-15
```
sudo mount -t ntfs /dev/sdb /home/ben/E-drive/
```

Should probably be:

```
sudo mount -t ntfs **/dev/sdb1** /home/ben/E-drive/
```

if that is wrong, post the results of ```
sudo fdisk -l
``` (that is a lower case L)


Edit: One other thing you could try is ```
sudo mount -t auto /dev/sdb1 /home/ben/E-drive/
```

---

### Post by SINZAR on 2010-05-15
I was hoping it was going to be that easy of a solution, but no dice.

```

sudo mount -t auto /dev/sdb1 /home/ben/E-drive/
mount: you must specify the filesystem type

```

```

sudo mount -t ntfs /dev/sdb1 /home/ben/E-drive/
NTFS signature is missing.
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

```

```

sudo fdisk -l

[B]Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x376e761e[/B]

   Device Boot      Start         End      Blocks   Id  System
**/dev/sdb1               1       38914   312570168+  42  SFS**

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x42de42dd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7785    62525550+   7  HPFS/NTFS
/dev/sda2            7785       30401   181668545+   f  W95 Ext'd (LBA)
/dev/sda5           12749       30401   141797691    7  HPFS/NTFS
/dev/sda6            7785       12539    38188032   83  Linux
/dev/sda7           12539       12748     1681408   82  Linux swap / Solaris

Partition table entries are not in disk order

```

Odd that it's coming up as 'sfs'...

---

### Post by Ozymandias_117 on 2010-05-15
Maybe try it without the type switch at all?

```
sudo mount /dev/sdb1 /home/ben/E-drive/
```

Just wondering, since when you used -t auto it acted like it wasn't using auto...

---

### Post by cap10Ibraim on 2010-05-15
the obvious question what's the last thing you changed before this happened can you track any modification or update ?

---

### Post by jkxx on 2010-05-15
I'm not sure this will help but if you can, boot to windows and have it run chkdsk on that drive (tell windows to do it if it doesn't automatically). Then reboot and see if you are still getting the same errors.

---

### Post by jerome1232 on 2010-05-15
Just curious but I see a total of two NTFS partitions, how many ntfs partitions does Windows see, 3?

---

### Post by SINZAR on 2010-05-15
> **jkxx said:**
> I'm not sure this will help but if you can, boot to windows and have it run chkdsk on that drive (tell windows to do it if it doesn't automatically). Then reboot and see if you are still getting the same errors.

That was one of the first things I tried. Windows (Windows 7) didn't detect any problems with it.

> **cap10Ibraim said:**
> the obvious question what's the last thing you changed before this happened can you track any modification or update ?

The last things installed were a bunch of system updates. Since it was a fresh install without much work done to it yet, I'll likely re-install if this can't be sorted, and see if it does it again.

> **jerome1232 said:**
> Just curious but I see a total of two NTFS partitions, how many ntfs partitions does Windows see, 3?

Yeah Windows see's 3.

---

### Post by SINZAR on 2010-05-16
Well it looks like this is a lost cause. After further research into mounting SFS drives I see nothing but unanswered topics and people left hanging.

Given the importance of my second drive I can't reformat it and since Ubuntu can't mount it, I guess I'll have to live with Windows on this system :(

---

### Post by jerome1232 on 2010-05-16
The only thing I can think of would be to just copy your data off that thing, reformat it then copy it back, but from the sounds of it you don't have an external to do that with?

Wish I had more experience with ntfs to help you out.

---

### Post by ads2k2 on 2010-07-12
Ozymandias,
Just wanted to say thanks.  I installed Lynx and it automounted all my NTFS partitions, then I updated...  for some reason it stopped mounting my (NTFS) drives, I tried using ntfs-config and got no love.  Then I found this thread through the magic that is Google, and manually mounting worked like a charm.  So thanks for putting it out there.

---

### Post by ankcrimson on 2012-09-18
Hi
I faced a similar problem but got it fixed by this 
[http://www.makeuseof.com/tag/fix-corrupted-windows-ntfs-filesystem-ubuntu/](http://www.makeuseof.com/tag/fix-corrupted-windows-ntfs-filesystem-ubuntu/)

all i did was:


sudo apt-get install ntfsprogs

which installed ntfsprogs


then i used the following command:

sudo ntfsfix /dev/sda5



you can replace sda5 with your own drive number which is sda2

hope this solves the problem

---

