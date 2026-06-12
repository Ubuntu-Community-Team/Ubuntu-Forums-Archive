---
title: "Need help after xp reinstall."
date: 2010-12-29
forum: General Help
---

### Post by postdiction on 2010-12-29
hi,

I am running 10.10 x86.  I am dual booting with xp and had to reinstall xp.  I was able to restore my grub boot loader after reinstalling xp.  Now I can boot into both XP and 10.10 without problems.

However, something is messed up with my partitions.

When I do:  ```
sudo cfdisk /dev/sda
```

I get:
```
 FATAL ERROR: Bad primary partition 1: Partition ends in the final partial cylinder
                                                         Press any key to exit cfdisk

```

So then I tried fdisk

When I do:  ```
sudo fdisk /dev/sda
```

I get:
```
omitting empty partition (5)

WARNING: DOS-compatible mode is deprecated. It's strongly recommended to
         switch off the mode (command 'c') and change display units to
         sectors (command 'u').
```


Running a "p" for print command I get:

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe4f2e4f2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1537    12345448+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            1538        9730    65802240    5  Extended
Partition 2 does not end on cylinder boundary.
/dev/sda3            3895        9729    46867456    b  W95 FAT32
Partition 3 does not end on cylinder boundary.
/dev/sda5            1538        3695    17325056   83  Linux
/dev/sda6            3695        3894     1604608   82  Linux swap / Solaris

```

Everything on my computer works fine and I am able to access all partitions without problem but, these errors make me nervous and I was wondering how I could fix them?

Any help would be appreciated

---

### Post by no2498 on 2010-12-29
i am not a guru in any way
but can you unplug your printer
see if it goes away

---

### Post by wilee-nilee on 2010-12-29
sda is the mbr not a partition. If its working give yourself time to break it and come back. :)

---

### Post by postdiction on 2010-12-29
> **no2498 said:**
> i am not a guru in any way
but can you unplug your printer
see if it goes away

Is this some type of joke?

---

### Post by postdiction on 2010-12-29
> **wilee-nilee said:**
> sda is the mbr not a partition. If its working give yourself time to break it and come back. :)

Umm....thanks but not really helping me out.

---

### Post by wilee-nilee on 2010-12-29
> **postdiction said:**
> Umm....thanks but not really helping me out.

I think you have no errors you are just not using the tools without understanding.

---

### Post by postdiction on 2010-12-29
> **wilee-nilee said:**
> I think you have no errors you are just not using the tools without understanding.

Okay I see what you are saying but from my understanding, that is how one uses cfdisk and fdisk. 

how do you propose I use fdisk and cfdisk to edit the partitions on the drive /dev/sda?

IMO my partition table is messed up and that is why cfdisk borks.

thanks for replying,

postdiction

---

### Post by dcstar on 2010-12-30
> **postdiction said:**
> 
.........
Everything on my computer works fine and I am able to access all partitions without problem but, these errors make me nervous and I was wondering how I could fix them?


[LIST=1]
[*]Stop being nervous - your system is working.
[*]Don't try to "fix" things that aren't causing problems.
[/LIST]

---

