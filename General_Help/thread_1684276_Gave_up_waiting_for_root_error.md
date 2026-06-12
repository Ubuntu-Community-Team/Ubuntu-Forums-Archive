---
title: "Gave up waiting for root error"
date: 2011-02-08
forum: General Help
---

### Post by murrellr on 2011-02-08
I have been trying to update my server from 6.06 server to 10.04 server.  My attempts have been complicated by versions later than 6.06 not being able to properly read my CD-ROM.  I used the 'do-release-upgrade' mechanism to upgrade to from 6.06 to 8.04 and then to 10.04.  8.04 loaded OK, but 10.04 fails to boot with the surprisingly common "Gave up waiting for root device" error.  It stops at the built-in shell prompt.  If I exit from the shell, it seems to boot up normally.

I tried all the fixes suggested in other threads, but none of these helped.  I have verified that the boot partition is /dev/sda1 and the UUID for the partition is correct.

My system is an older IBM eServer xSeries 350 with quad 700MHz XEON processors and a 36GB SCSI drive.  This system properly installed from the 6.06 CD and boots under this version without problems.  So I have some questions.  Only the first one needs an answer.

1. What do I need to do to get my system to boot properly?

2. Why was this software released with this error?

3. Why wasn't the faulty loader pulled from the release until it was fixed?

4. Is it possible to revert to the 6.06 loader, which works fine?

5. Why doesn't the loader attempt to try something else that should work instead of just giving up?

---

### Post by wojox on 2011-02-08
Run these and post them back and let's see:

```
sudo fdisk -l
```

```
sudo blkid
```

```
cat /etc/fstab
```

---

### Post by murrellr on 2011-02-09
sudo fdisk -l

```
Disk /dev/sda: 36.4 GB, 36420075520 bytes
255 heads, 63 sectors/track, 4427 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002a584

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4244    34089898+  83  Linux
/dev/sda2            4245        4427     1469947+   5  Extended
/dev/sda5            4245        4427     1469916   82  Linux swap / Solaris

```

sudo blkid

```
/dev/sda1: UUID="9cf521a2-8b4d-433b-b3c2-b55add3f551b" TYPE="ext3" 
/dev/sda5: UUID="dfd644d4-0cb6-4bb3-859e-f98d42df1c83" TYPE="swap" 

```

cat /etc/fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1 -- converted during upgrade to edgy
UUID=9cf521a2-8b4d-433b-b3c2-b55add3f551b / ext3 defaults,errors=remount-ro 0 1
# /dev/sda5 -- converted during upgrade to edgy
UUID=dfd644d4-0cb6-4bb3-859e-f98d42df1c83 none swap sw 0 0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

---

### Post by murrellr on 2011-02-17
I'm moving my website to a commercial hosting site and retiring my server.  I'm tired of the grief from struggling with free software and am giving up on Linux entirely.  So long, and thanks for the fish.

---

### Post by User3k on 2011-02-17
Does anyone want to point out that there is a good chance the commercial server will be running Linux? Nah, don't spoil the surprise :)

---

### Post by matt_symes on 2011-02-18
Hi

Did you try changing the rootdelay grub2 boot option ?

Add

```
rootdelay=90
```

to your kernel boot line. (90 seconds)

It might just be that maverick expects to run on newer hardware and has to be configured differently for older hardware (i.e. changing defaulted tolerances).

After all, try running windows 7 on older hardware.

Kind regards

---

