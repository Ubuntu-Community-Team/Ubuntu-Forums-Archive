---
title: "Extended logical partitioning"
date: 2009-10-23
forum: General Help
---

### Post by texas.chef94 on 2009-10-23
Indulge me just a moment as an example explains my concern rather then bunch confusing statements
On a 160 GB HD with windows at 15GB, a swap 2GB and Ubuntu 9.04 10 GB in a dual boot, Assuming one took the remainder that was unallocated and created an extended partition and within that extended made the remainder Logical to create additional Linux OS. Everything being equal given the OS in question recognizing XP and Ubuntu would I normally have a grub MBR concern.
Or am I all wet in my understanding of Extended/logical
Please advise and my skin is thick so fire away
Thanks in advance and if you have a better approach to utilizing this HD please give me that as well

---

### Post by Bartender on 2009-10-23
The existing partitions are all primary?
You know of course that you're limited to 4 primaries, or 3 primaries and an extended, correct?  I've had the GParted partitioner get very uncooperative after 3 primaries, so I consider 2 primaries as the upper limit.

IMO, a primary swap partition just doesn't make any sense.

If you have problems with multi-booting, the extended partition won't be the cause.

EDIT: if that swap is _not_ a primary partition, you can't make another extended partition.

---

### Post by undecim on 2009-10-23
from what I understand (and I could be all wrong about this... If i am, someone please correct me) an extended partition is a 4th partition on a drive that is divided into more than one logical partitions. This gives the ability to have more than 4 partitions on one drive, but with the disadvantage that some legacy OSs (DOS?) won't be able to read them.

Also, with Linux, you can share 1 swap partition between two, meaning if you just wanted another Linux install on that drive, it would only require 1 more partition, which wouldn't have to be extended/logical

Just make sure you never hibernate FROM one Linux and INTO another. I don't know if there are safegaurds against that. (If there aren't, there should be)

---

### Post by texas.chef94 on 2009-10-23
> **Bartender said:**
> The existing partitions are all primary?
You know of course that you're limited to 4 primaries, or 3 primaries and an extended, correct?  I've had the GParted partitioner get very uncooperative after 3 primaries, so I consider 2 primaries as the upper limit.

IMO, a primary swap partition just doesn't make any sense.

If you have problems with multi-booting, the extended partition won't be the cause.

EDIT: if that swap is _not_ a primary partition, you can't make another extended partition.

I certainly appreciate that speedy and informative reply. I just had never considered swap in any other capacity. And know what you mean about gparted. Thanks a lot

---

### Post by az on 2009-10-23
Back in the day, the code that was executed on an msdos partitioned drive would direct the BIOS to boot the first partition on the drive if no other partition was flagged as "boot".  If two or more partitions were flagged as "boot", then the first one it encountered was booted.  

The only purpose of the boot flag was to direct the BIOS to boot a partition that was not the first one, if that's what you wanted to do.

Grub overwrites that MBR code with it's own.  Since GRUB lives both on the first block of the drive (stage 1) and on the partition you are booting (stage 1.5 and 2) the boot flag is irrelevant.  

So create as many partitions you want/can and use grub to boot them at will!

---

### Post by QLee on 2009-10-23
[QUOTE=texas.chef94]Indulge me just a moment as an example explains my concern rather then bunch confusing statements[/QUOTE]

Okay Allen, I think I followed your example.

[QUOTE=texas.chef94]On a 160 GB HD with windows at 15GB, a swap 2GB and Ubuntu 9.04 10 GB in a dual boot, Assuming one took the remainder that was unallocated and created an extended partition and within that extended made the remainder Logical to create additional Linux OS.[/QUOTE] 

This is a fairly common way to provision a system, the system I'm typing this on is something similar, although it has three physical drives, some of each one is partitioned with an extended partition and those extended partitions have logical partitions.

[QUOTE=texas.chef94]Everything being equal given the OS in question recognizing XP and Ubuntu would I normally have a grub MBR concern.[/QUOTE]

I'm not sure what you mean by this question because I don't know what you mean by "OS in question" Do you mean one of those "other" OS that you intend to put in one of the logical partitions? 

The MBR part of GRUB tells grub where to go (which partition) for your /boot so it can find the rest of the files it needs. It only changes if you rewrite GRUB to the MBR with a different location for /boot (i.e. when you install another OS it is possible to choose to do this)

[QUOTE=texas.chef94]Or am I all wet in my understanding of Extended/logical[/QUOTE]

Seems to me you understand it correctly.

[QUOTE=texas.chef94]Please advise and my skin is thick so fire away[/QUOTE]

Nah, not my style for you to require a flamesuit to read my reply .

[QUOTE=texas.chef94]Thanks in advance and if you have a better approach to utilizing this HD please give me that as well[/QUOTE]

For multiboot, I prefer a separate boot partition, but people have different opinions on that and there can be valid reasons for either having one or not. I don't mount my boot directory in the OS that I have booted, doing it that way I have to manually change my GRUB Menu when I add an OS and/or upgrade a kernel to a new version but my GRUB menu remains the same and continues to boot all the OSs that work. This method might be too convoluted for someone until they understand well how things work and I know you have been struggling with this for a while. May I say, good for you for sticking with it!

Note: "Better" is subjective. If you told us exactly the way you have chosen to partition, then we could give opinions on what might be better (and likely argue about it) but whatever is easiest for you with the understanding you currently hold is probably better than something you might not understand fully and thus make an error. We don't want you to get into a non-booting Ubuntu situation after installing another OS. Happily, I know you already know how to use a live CD.

---

### Post by QLee on 2009-10-23
[QUOTE=undecim]from what I understand (and I could be all wrong about this... If i am, someone please correct me) an extended partition is a 4th partition on a drive that is divided into more than one logical partitions. This gives the ability to have more than 4 partitions on one drive, but with the disadvantage that some legacy OSs (DOS?) won't be able to read them.[/QUOTE]

The extended partition does not have to be the 4th. On this system I have one drive that has only an extended partition (the 1st) with logical partitions.

---

