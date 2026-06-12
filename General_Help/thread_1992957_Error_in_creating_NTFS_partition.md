---
title: "Error in creating NTFS partition"
date: 2012-06-01
forum: General Help
---

### Post by AAEIV on 2012-06-01
Hello to everyone!

I am trying to create an NTFS partition, however an error occurs.
My present partition is as follows:

[img]http://i.imgur.com/kBEMt.png[/img]

I used DISK UTILITY to create an NTFS partition, but the following erros comes up:

```
Error creating partition: helper exited with exit code 1: In part_add_partition: device_file=/dev/sda, start=130408250368, size=59999519744, type=0x07
Entering MS-DOS parser (offset=0, size=250059350016)
MSDOS_MAGIC found
looking at part 0 (offset 32256, size 10478974464, type 0x12)
new part entry
looking at part 1 (offset 10479468544, size 119927734272, type 0x06)
new part entry
looking at part 2 (offset 130408250368, size 116168590336, type 0x05)
Entering MS-DOS extended parser (offset=130408250368, size=116168590336)
readfrom = 130408250368
MSDOS_MAGIC found
readfrom = 210406211584
MSDOS_MAGIC found
readfrom = 218405859840
MSDOS_MAGIC found
readfrom = 130411814400
No MSDOS_MAGIC found
Exiting MS-DOS extended parser
looking at part 3 (offset 246576840704, size 3481272320, type 0x12)
new part entry
Exiting MS-DOS parser
MSDOS partition table detected
containing partition table scheme = 1
got it
Error: Invalid partition table on /dev/sda -- wrong signature 0.
ped_disk_new() failed
```

I used the command ```
sudo fdisk -l
```
which produces the output

```
omitting empty partition (8)

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbb762c7e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1274    10233373+  12  Compaq diagnostics
/dev/sda2   *        1275       15855   117116928    6  FAT16
/dev/sda3           15855       29978   113445889    5  Extended
/dev/sda4           29978       30402     3399680   12  Compaq diagnostics
/dev/sda5           23150       25581    19529728   83  Linux
/dev/sda6           25581       26553     7811072   82  Linux swap / Solaris
/dev/sda7           26554       29978    27509760   83  Linux
```

I also used GPARTED but even there things are not working.

[img]http://www.ftpimg.com/img/gzZU.png[/img]

Finally I used an Ubuntu 12.04 Live CD, but the output remains the same. I cannot even create FAT or ext4...

Any ideas on this?

---

### Post by coffeecat on 2012-06-01
> **AAEIV said:**
> Any ideas on this?

Almost certainly an illegality in the partition table. The output of fdisk will help, but the output you've posted gives start and end figures in cylinders. We need sectors to be able to see where the problem is. Post the output of:

```
sudo fdisk -lu
```

Which version of Ubuntu are you using?

**EDIT**: forget the last question. :) I can see from the theming of your Gparted window that you are running 10.04/Lucid. That explains why "sudo fdisk -l" gave output in cylinders. Post "sudo fdisk -lu" and we'll get the information we need.

---

### Post by AAEIV on 2012-06-01
Thank's a lot for your reply!
The output I get is 

```
omitting empty partition (8)

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbb762c7e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    20466809    10233373+  12  Compaq diagnostics
/dev/sda2   *    20467712   254701567   117116928    6  FAT16
/dev/sda3       254703614   481595391   113445889    5  Extended
/dev/sda4       481595392   488394751     3399680   12  Compaq diagnostics
/dev/sda5       371890176   410949631    19529728   83  Linux
/dev/sda6       410951680   426573823     7811072   82  Linux swap / Solaris
/dev/sda7       426575872   481595391    27509760   83  Linux

Disk /dev/sdb: 4009 MB, 4009754624 bytes
145 heads, 48 sectors/track, 1125 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          48     7831551     3915752    b  W95 FAT32
```

---

### Post by coffeecat on 2012-06-01
- EDIT - you edited in the three lines that were needed. I'll study it and post back.

---

### Post by coffeecat on 2012-06-01
The three partition illegalities that are commonly seen when Gparted shows "unallocated" in what is clearly a drive with valid partition are: overlapping partitions, a partition end sector beyond the physical end boundary of the drive, and a primary partition inside an extended partition. I can see no evidence of any of these.

Your Disk Utility error included this:

```
Error: Invalid partition table on /dev/sda -- wrong signature 0.
```

I'm tempted to suggest using a utility called [fixparts]("http://www.rodsbooks.com/fixparts/"). This is usually used to fix faulty partitions, but you have none - the problem seems to be in the partition table signature. If you run fixparts and simply 'w' to write the partition table and exit, this will *probably* fix the problem. However, I suggest you hold off for a little while. I'd like to get someone else to have a look to see if there's anything I've missed. I'll pm them now. In the meantime have a read of the fixparts link and it would do no harm to backup your partition table with the sdisk command given there.

---

### Post by AAEIV on 2012-06-01
Thank you very much for your time!

---

### Post by coffeecat on 2012-06-01
I mistyped sdisk for sfdisk in my previous post, but all the details are in the fixparts tutorials page. I've pm'd two other forum members but they're both offline at the moment, and I have to log off for a couple of hours or more now, but I'm sure we'll get this fixed! :)

---

### Post by Quackers on 2012-06-01
Hi, I think Fixparts might fix things up, but the instructions of post #11 (by delance) in the thread below may be even easier (thanks coffeecat!). I suspect they may both do the same thing.

[https://answers.launchpad.net/ubuntu/+question/113539](https://answers.launchpad.net/ubuntu/+question/113539)

---

### Post by AAEIV on 2012-06-01
I typed the command

```
sudo fdisk /dev/sda
``` 

I got hte output

```
omitting empty partition (8)

WARNING: DOS-compatible mode is deprecated. It's strongly recommended to
         switch off the mode (command 'c') and change display units to
         sectors (command 'u').
```

I gave w

```
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 16: Device or resource busy.
The kernel still uses the old table. The new table will be used at
the next reboot or after you run partprobe(8) or kpartx(8)
Syncing disks.
```

I run GParted and the partition table was created.
I modified the free space into NTFS and guess what...

No error occured!!!:guitar:

I started windows and I can see 55sweet GB of space!!!

Thank you very much for your time guys!

You were really helpful!!!

---

### Post by Quackers on 2012-06-01
Excellent! That's good to hear :-)
Coffeecat will be glad too.

---

### Post by coffeecat on 2012-06-01
> **Quackers said:**
> 
Coffeecat will be glad too.

He is! :)

@AAEIV, Quackers and I discussed this by pm and we're fairly sure that running fixparts and 'w' simply runs fdisk and 'w' in the background, so they both come to the same thing. My guess is that you would have seen fewer blood-curdling messages with fixparts though!

Anyway, I'm glad it's fixed and don't forget to bookmark that fixparts link - you never know when you might need it. :wink:

---

