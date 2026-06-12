---
title: "PANIC - Grub messed up, no boot"
date: 2011-09-23
forum: General Help
---

### Post by Quaxo76 on 2011-09-23
I have a system with several partitions, I had a multi-boot set up (two Ubuntu's and a Windows). After trying to repair Windows (which wasn't working), Grub2 was of course removed; I tried reinstalling it, and now when I boot the computer, all I get is the GRUB shell - you know, black screen and the ```
grub>
``` prompt.
I'm scared to experiment because I don't want to mess up the partitions and loose data. How do I reinstall Grub from the shell?

Thank you,
Cristian

---

### Post by lordbux on 2011-09-23
> **Quaxo76 said:**
> I have a system with several partitions, I had a multi-boot set up (two Ubuntu's and a Windows). After trying to repair Windows (which wasn't working), Grub2 was of course removed; I tried reinstalling it, and now when I boot the computer, all I get is the GRUB shell - you know, black screen and the ```
grub>
``` prompt.
I'm scared to experiment because I don't want to mess up the partitions and loose data. How do I reinstall Grub from the shell?

Thank you,
Cristian


Pop in your live cd and then run ```
sudo update-grub
```
i got mine corrected when i did  this.

---

### Post by Quaxo76 on 2011-09-23
> **lordbux said:**
> Pop in your live cd and then run ```
sudo update-grub
```
i got mine corrected when i did  this.

It gives this error:```
/usr/sbin/grub-probe: error: cannot stat `aufs'.
```

Cristian

---

### Post by drs305 on 2011-09-23
You can't run the update-grub command from the LiveCD to update your normal installation.

To see what has happened to your system, please download and run the Boot Info script and post the contents of the RESULTS.txt file. The script and instructions are available by clicking the "BIS" link in my signature line.

---

### Post by Quaxo76 on 2011-09-23
> **drs305 said:**
> 
To see what has happened to your system, please download and run the Boot Info script and post the contents of the RESULTS.txt file. The script and instructions are available by clicking the "BIS" link in my signature line.

I downloaded and ran it, I got this output: ```
boot_info_script verion: 0.60        [17 may 2011]


"gawk" could not be found, using "busybox awk" instead.
This may lead to unreliable results.

Identifying MBRs...
Computing partition Table of /dev/sda...
```
And it stops there. It's been sitting there for 5 minutes, with no disk activity.
The partitions are still there, I can manually mount them and see the contents, so I'm not loosing hope for now...

Can't I use chroot from the livecd?

Cristian

---

### Post by Quaxo76 on 2011-09-23
Wait... more problems...
I had an idea: there was a pretty much unused 20GB partition on the drive, so I thought I'd just install a new Ubuntu on that partition, and let it recreate grub during installation, to get the system running again.
But when I ran GParted from the live cd, it detected about 250 partitions on the drive. Most of them are just "phantom copies" of two 40-50GB partitions I really have. 
So, it looks like the partition table is messed up too. There must be some sort of "loop" there. Any idea how to fix/rebuild it?  I remember many years ago I rebuilt one (MS-Dos) by hand using a hex-editor, it took me two weeks... but I think I'm too old for that now... :(

Cristian

---

### Post by Quackers on 2011-09-23
Something seems to be wrong. The script should only take a few seconds to run.
As it's getting stuck at reading the partition info I suspect that you have a partition problem.
Please open a terminal in the live desktop and post the results from this, if any ```
sudo fdisk -lu
```

---

### Post by Quaxo76 on 2011-09-23
Here's the output. It's badly messed up, as I said there are hundreds of partitions. fdisk only shows the firsts 60...

```
ubuntu@ubuntu:~$ sudo fdisk -lu
Warning: omitting partitions after #60.
They will be deleted if you save this partition table.

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x9bca9bca

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    94928016    47462984+   7  HPFS/NTFS
/dev/sda2        94928024   129092767    17082372   83  Linux
/dev/sda3       129437694   976773119   423667713    5  Extended
Partition 3 does not start on physical sector boundary.
/dev/sda5       190996848   194900579     1951866   82  Linux swap / Solaris
/dev/sda6       194900643   276816014    40957686   83  Linux
Partition 6 does not start on physical sector boundary.
/dev/sda7       276817920   308142079    15662080   83  Linux
/dev/sda8       308144128   369606655    30731264   83  Linux
/dev/sda9       369607518   459282284    44837383+  83  Linux
Partition 9 does not start on physical sector boundary.
/dev/sda10      459282348   542049164    41383408+  83  Linux
Partition 10 does not start on physical sector boundary.
/dev/sda11      369607518   459282284    44837383+  83  Linux
Partition 11 does not start on physical sector boundary.
/dev/sda12      459282348   542049164    41383408+  83  Linux
Partition 12 does not start on physical sector boundary.
/dev/sda13      369607518   459282284    44837383+  83  Linux
Partition 13 does not start on physical sector boundary.
/dev/sda14      459282348   542049164    41383408+  83  Linux
Partition 14 does not start on physical sector boundary.
/dev/sda15      369607518   459282284    44837383+  83  Linux
Partition 15 does not start on physical sector boundary.
/dev/sda16      459282348   542049164    41383408+  83  Linux
Partition 16 does not start on physical sector boundary.
/dev/sda17      369607518   459282284    44837383+  83  Linux
Partition 17 does not start on physical sector boundary.
/dev/sda18      459282348   542049164    41383408+  83  Linux
Partition 18 does not start on physical sector boundary.
/dev/sda19      369607518   459282284    44837383+  83  Linux
Partition 19 does not start on physical sector boundary.
/dev/sda20      459282348   542049164    41383408+  83  Linux
Partition 20 does not start on physical sector boundary.
/dev/sda21      369607518   459282284    44837383+  83  Linux
Partition 21 does not start on physical sector boundary.
/dev/sda22      459282348   542049164    41383408+  83  Linux
Partition 22 does not start on physical sector boundary.
/dev/sda23      369607518   459282284    44837383+  83  Linux
Partition 23 does not start on physical sector boundary.
/dev/sda24      459282348   542049164    41383408+  83  Linux
Partition 24 does not start on physical sector boundary.
/dev/sda25      369607518   459282284    44837383+  83  Linux
Partition 25 does not start on physical sector boundary.
/dev/sda26      459282348   542049164    41383408+  83  Linux
Partition 26 does not start on physical sector boundary.
/dev/sda27      369607518   459282284    44837383+  83  Linux
Partition 27 does not start on physical sector boundary.
/dev/sda28      459282348   542049164    41383408+  83  Linux
Partition 28 does not start on physical sector boundary.
/dev/sda29      369607518   459282284    44837383+  83  Linux
Partition 29 does not start on physical sector boundary.
/dev/sda30      459282348   542049164    41383408+  83  Linux
Partition 30 does not start on physical sector boundary.
/dev/sda31      369607518   459282284    44837383+  83  Linux
Partition 31 does not start on physical sector boundary.
/dev/sda32      459282348   542049164    41383408+  83  Linux
Partition 32 does not start on physical sector boundary.
/dev/sda33      369607518   459282284    44837383+  83  Linux
Partition 33 does not start on physical sector boundary.
/dev/sda34      459282348   542049164    41383408+  83  Linux
Partition 34 does not start on physical sector boundary.
/dev/sda35      369607518   459282284    44837383+  83  Linux
Partition 35 does not start on physical sector boundary.
/dev/sda36      459282348   542049164    41383408+  83  Linux
Partition 36 does not start on physical sector boundary.
/dev/sda37      369607518   459282284    44837383+  83  Linux
Partition 37 does not start on physical sector boundary.
/dev/sda38      459282348   542049164    41383408+  83  Linux
Partition 38 does not start on physical sector boundary.
/dev/sda39      369607518   459282284    44837383+  83  Linux
Partition 39 does not start on physical sector boundary.
/dev/sda40      459282348   542049164    41383408+  83  Linux
Partition 40 does not start on physical sector boundary.
/dev/sda41      369607518   459282284    44837383+  83  Linux
Partition 41 does not start on physical sector boundary.
/dev/sda42      459282348   542049164    41383408+  83  Linux
Partition 42 does not start on physical sector boundary.
/dev/sda43      369607518   459282284    44837383+  83  Linux
Partition 43 does not start on physical sector boundary.
/dev/sda44      459282348   542049164    41383408+  83  Linux
Partition 44 does not start on physical sector boundary.
/dev/sda45      369607518   459282284    44837383+  83  Linux
Partition 45 does not start on physical sector boundary.
/dev/sda46      459282348   542049164    41383408+  83  Linux
Partition 46 does not start on physical sector boundary.
/dev/sda47      369607518   459282284    44837383+  83  Linux
Partition 47 does not start on physical sector boundary.
/dev/sda48      459282348   542049164    41383408+  83  Linux
Partition 48 does not start on physical sector boundary.
/dev/sda49      369607518   459282284    44837383+  83  Linux
Partition 49 does not start on physical sector boundary.
/dev/sda50      459282348   542049164    41383408+  83  Linux
Partition 50 does not start on physical sector boundary.
/dev/sda51      369607518   459282284    44837383+  83  Linux
Partition 51 does not start on physical sector boundary.
/dev/sda52      459282348   542049164    41383408+  83  Linux
Partition 52 does not start on physical sector boundary.
/dev/sda53      369607518   459282284    44837383+  83  Linux
Partition 53 does not start on physical sector boundary.
/dev/sda54      459282348   542049164    41383408+  83  Linux
Partition 54 does not start on physical sector boundary.
/dev/sda55      369607518   459282284    44837383+  83  Linux
Partition 55 does not start on physical sector boundary.
/dev/sda56      459282348   542049164    41383408+  83  Linux
Partition 56 does not start on physical sector boundary.
/dev/sda57      369607518   459282284    44837383+  83  Linux
Partition 57 does not start on physical sector boundary.
/dev/sda58      459282348   542049164    41383408+  83  Linux
Partition 58 does not start on physical sector boundary.
/dev/sda59      369607518   459282284    44837383+  83  Linux
Partition 59 does not start on physical sector boundary.
/dev/sda60      459282348   542049164    41383408+  83  Linux
Partition 60 does not start on physical sector boundary.

Partition table entries are not in disk order

Disk /dev/sdb: 16.1 GB, 16053960192 bytes
16 heads, 32 sectors/track, 61240 cylinders, total 31355391 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32    31355390    15677679+   b  W95 FAT32

```

Cristian

---

### Post by Quackers on 2011-09-23
I have no idea what is causing that! :-)
I see that all those later entries appear to be copies of sda9 and sda10 - or at least, half of them have the same starting/finishing sectors as sda9 or sda10.

Very odd! I've never seen anyting like that. We'd better wait for further advice, I think ;)

---

### Post by Quaxo76 on 2011-09-23
:( Yes, I noticed there are a couple hundred copies of those two. I don't know if the partitions that were *after* those two, are still accessible.
I hope there's a way to have the system "rebuild" a new partition table... Or wasn't there a backup copy kept on the disk somewhere just for these problems?

Cristian

---

### Post by drs305 on 2011-09-23
There are a few forum members who know Grub very well and also understand partition tables, but they may not see this post. The problem is only indirectly related to Grub.

I'd recommend starting a new thread with a title that reflects a partition problem and it shows dozens/hundreds of partitions. That should attract more viewers knowledgeable with partition reconstruction.

---

### Post by Quaxo76 on 2011-09-23
> **drs305 said:**
> 

I'd recommend starting a new thread with a title that reflects a partition problem and it shows dozens/hundreds of partitions. That should attract more viewers knowledgeable with partition reconstruction.

Will do, thanks!

Cristian

---

