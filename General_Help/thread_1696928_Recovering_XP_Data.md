---
title: "Recovering XP Data"
date: 2011-02-28
forum: General Help
---

### Post by absolute linux noob on 2011-02-28
So I just installed 10.10 on my Dell XPS M1530 which was previously running XP SP3.

Initially, I installed with a manually configured partition table. /dev/sda was a 320GB HDD completely assigned to XP. I shrunk that down to 280GB, leaving 1GB for a swap area, 4GB shared container configured as a FAT32, and 35GB ext4 for Ubuntu. This meant I had:
/dev/sda[INDENT]/dev/sda1: 280GB XP
/dev/sda2: 35 GB ext4
/dev/sda3: 4 GB FAT32
/dev/sda4: 1 GB Swap
[/INDENT]I then proceeded to install on the 35GB. Evidently, I screwed up somewhere along the way, and/or GRUB had problems, as I was only able to boot XP. Booting from the Live CD, however, showed that Ubuntu was on there. Rather than troubleshoot, I decided to just use the automatic partitioning system to re-install Ubuntu instead. I was given the option to use the entire partition or disk, which had the same result, or to split the current partition, which it said was splitting the 35GB ext4. So I chose to give the Ubuntu that was already on there ~2GB (the minimum) and the new install the remainder ~ 33GB. Unfortunately though, evidently it really meant the entire disk. The next time it booted I found Ubuntu 10.10 was now my only OS and it's occupying the whole 320GB, or so the file systems folder states. This brings me to my current problem.

Obviously, I had backed up XP, but there is a lot of data (not so important, but definitely desirable) that I had not gotten around to backing up for this month (my next backup was scheduled for today :confused:  silly me). That said, I am now hoping that it is possible to retrieve my XP data. Again, I am not actually certain that the partition is gone, it COULD be merely booting issues, but the file systems folder does say it has ~300GB+ free. EDIT: *now I look at it, it actually says there is one disk, that is ~285GB. Maybe I overwrote the XP partition and the other Ubuntu partition (the 35GB) still exists. Either way I'm still lost without my data on the XP partition.* I'm also completely happy with nuking Ubuntu as I have literally just got the raw install running as I just discovered the problem in the last hour.

I'm happy to provide any terminal results etc. as required, just try to be as explicit as possible in your instructions as I haven't experienced Ubuntu for about 3 major updates (7.0?) and my use of Linux has been somewhat limited. That is, you will need to spell everything out for me.

Thanks in advance, I'll check back here at least daily.

---

### Post by decrepit on 2011-02-28
I think the first thing anybody that can help you will want is the result of

```
sudo fdisk -l
```

That will show all the partitions you have and their filesystem type.

---

### Post by Arand on 2011-02-28
It is likely that much of it is lost, but you may have some luck with [_[COLOR="Blue"]testdisk[/COLOR]_]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step") or [[COLOR="blue"]_PhotoRec_[/COLOR]]("http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step")

They should both be available under the "testdisk" package if you boot an ubuntu liveCD (might have to enable universe repository...), or preinstalled on the dedicated [[COLOR="Blue"]_SystemRescueCD_[/COLOR]]("http://www.sysresccd.org/")

- arand

---

### Post by celldweller1591 on 2011-02-28
SystemrescueCD is an option. It really works for everyone :)
@yusof125: nice one !

---

### Post by absolute linux noob on 2011-02-28
> Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c324c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       37767   303355904   83  Linux
/dev/sda2           37767       38914     9212929    5  Extended
/dev/sda5           37767       38914     9212928   82  Linux swap / Solaris


I'll now proceed to try as suggested. Will report back. Thanks

---

### Post by Hedgehog1 on 2011-02-28
> 
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, [COLOR="DarkRed"]**_38913_**[/COLOR] cylinders
...
Device Boot Start End Blocks Id System
/dev/sda1 * [COLOR="DarkRed"]**_1_**[/COLOR] 37767 303355904 83 Linux
/dev/sda2 37767 [COLOR="DarkRed"]**_38914_**[/COLOR] 9212929 5 Extended
/dev/sda5 37767 [COLOR="DarkRed"]**_38914_**[/COLOR] 9212928 82 Linux swap / Solaris


Is it just me, or is the entire drive Ubuntu now?

---

