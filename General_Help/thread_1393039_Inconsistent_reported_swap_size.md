---
title: "Inconsistent reported swap size ?"
date: 2010-01-28
forum: General Help
---

### Post by slickvguy on 2010-01-28
Just curious about something...

When I setup Intrepid (upgraded to Jaunty now), I chose to create a swap partition. I don't remember the size I specified. Here's what I'm confused about. When I do 'cat /proc/meminfo' or 'free' or use the system monitor, it reports my swap size as 1262304 KB (i.e. 1.2GB). But if I do a 'fdisk -l', the partition size is reported as 746991 blocks (of 1024 bytes) and if I use the partition editor it says it's 729.48MB. XP disk mgmt shows it as app. 700MB too.

Can someone explain this to me? 

Thank you.

---

### Post by x33a on 2010-01-28
please post the full output of these commands
```
sudo fdisk -l
free
cat /proc/meminfo
```

---

### Post by slickvguy on 2010-01-28
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb9bbb9bb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   c  W95 FAT32 (LBA)
/dev/sda2            2551        9729    57665317+   f  W95 Ext'd (LBA)
/dev/sda5            2551        7661    41054076    b  W95 FAT32
/dev/sda6            7662        9636    15864156   83  Linux
/dev/sda7            9637        9729      746991   82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa06338c8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241    7  HPFS/NTFS

```


```
             total       used       free     shared    buffers     cached
Mem:       2061308     455196    1606112          0      25284     172732
-/+ buffers/cache:     257180    1804128
Swap:      1262304          0    1262304

```


```
MemTotal:        2061308 kB
MemFree:         1607732 kB
Buffers:           25372 kB
Cached:           172744 kB
SwapCached:            0 kB
Active:           249120 kB
Inactive:         159956 kB
Active(anon):     184536 kB
Inactive(anon):    32276 kB
Active(file):      64584 kB
Inactive(file):   127680 kB
Unevictable:           8 kB
Mlocked:               8 kB
HighTotal:       1191396 kB
HighFree:         805008 kB
LowTotal:         869912 kB
LowFree:          802724 kB
SwapTotal:       1262304 kB
SwapFree:        1262304 kB
Dirty:                28 kB
Writeback:             0 kB
AnonPages:        210968 kB
Mapped:            52156 kB
Slab:              18776 kB
SReclaimable:      10264 kB
SUnreclaim:         8512 kB
PageTables:         2580 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     2292956 kB
Committed_AS:     790904 kB
VmallocTotal:     122880 kB
VmallocUsed:       26204 kB
VmallocChunk:      74740 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       4096 kB
DirectMap4k:       20472 kB
DirectMap4M:      884736 kB
```

---

### Post by john newbuntu on 2010-01-29
Did you happen to repartition any of your devices?  Try reformatting your swap partition and re-check.

sudo swapoff -a
sudo /sbin/mkswap /dev/sda7
sudo swapon -a
swapon -s[FONT=Verdana]
free
[/FONT]

---

### Post by slickvguy on 2010-01-29
> **john newbuntu said:**
> Did you happen to repartition any of your devices?  Try reformatting your swap partition and re-check.

sudo swapoff -a
sudo /sbin/mkswap /dev/sda7
sudo swapon -a
swapon -s[FONT=Verdana]
free
[/FONT]

Tried this, but got an error message at 'sudo swapon -a':

swapon: cannot stat /dev/disk/by-uuid/600405ca-042b-4006-8c4a-79e3b5d49828: No such file or directory

Is it because the old swap's uuid is used in fstab?

What now?

---

### Post by slickvguy on 2010-01-29
> **slickvguy said:**
> Tried this, but got an error message at 'sudo swapon -a':

swapon: cannot stat /dev/disk/by-uuid/600405ca-042b-4006-8c4a-79e3b5d49828: No such file or directory

Is it because the old swap's uuid is used in fstab?

What now?

OK. Fixed it. Changed the UUID in /etc/fstab to the new one created.

```
slickvguy@anon-desktop:~$ free
             total       used       free     shared    buffers     cached
Mem:       2061308     457228    1604080          0      27596     175980
-/+ buffers/cache:     253652    1807656
Swap:       746980          0     746980
```

Voila!

I don't remember, but perhaps I did change the size of the preceding partition (larger)? Not sure.

Anyways...thank you.

---

### Post by slickvguy on 2010-01-29
Sh*t. I rebooted and the problem is back. :(

Could it be a geometry or translation/calc error of some sort?

fdisk gets it's info directly from the partition table - correct?
XP reports the same size.

Is it possible those programs are erring in the way they calculate the size?
How do those other programs get their info? I traced through a bit of kernel source code, but didn't see where. (swap header?). They probably all grab the info from the same initial source. It's not as if the two values are remotely close. Quite a difference.

---

### Post by slickvguy on 2010-01-29
Found a page describing the swapfile structure. In my swap's header, the last page (unsigned int) is set to 0x0002d97a. Multiplied by 4,096 (pagesize) + 1 page reserved + 3,072 bytes of filler at the end of the partition = 764,918,784 bytes. This is exactly what fdisk reports as the size of the partition. Therefore, the swapfile's header has the correct number of swap pages...and programs relying on that value would likely be correct.

So where is the 1.2GB number coming from? Is it stored somewhere (static) - or is it being determined on each boot?

---

### Post by john newbuntu on 2010-01-29
Interesting.  The swap didn't stick.  I am also guessing that "dmesg | grep -i swap" in your case will report 1.2GB as swap space.  Do you want to try re-running the mkswap command with the "-c" option to check the swap device for badblocks?
I am almost tempted to boot the machine with no swap and see what readings show up.
edit: or is this a bug with your version of Ubuntu??

---

### Post by slickvguy on 2010-01-29
Figured it out. Originally, I had the idea that maybe there was another file being added to the 7xx MB to total 1.2MB. It had to have been created by the system, because I know for sure that I never created a swap file - I only used the partition. 

Well....I was snooping around in /proc and looky what I found...

```

slickvguy@anon-desktop:~$ cat /proc/swaps
Filename				Type		Size	Used	Priority
/dev/ramzswap0                          partition	515324	0	100
/dev/sda7                               partition	746980	0	-1

```

Yeesh! How did THAT get there? I've got 2GB RAM. WTF?

Well, at least I now know where that 1.2GB figure is coming from and the discrepency.

Update: If you set COMPCACHE_SIZE="" (in /usr/share/initramfs-tools/conf.d/compcache) and sudo update-initramfs -u, you get rid of this. Finally.

---

### Post by john newbuntu on 2010-01-29
Aahh.   Thanks for sharing that.

---

