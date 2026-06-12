---
title: "Migrating quad-boot setup"
date: 2010-03-13
forum: General Help
---

### Post by Burillo on 2010-03-13
I know that these forums aren't M$ support forums, but any mention of Linux and open source there just ends up in "don't use Linux"-type replies, so i figured i should ask it here.

I have a quad-boot setup (Win7x64-Win7x64-K9.10x64-K9.10x64). I am in the process of migrating this setup to another (bigger) HDD. The Win7 system partitions were cloned using 3rd paty imaging software, Linux system partitions were cloned directly (cat /dev/sda5 > /dev/sdb5), data partitions were freshly created and populated with files copied from old partitions.

As the hard drive is bigger than previous one, i decided to add a little more space to Win7 system partitions. So when creating new partitions, i left 5GB unallocated space between them in order to grow the partitions later. I cloned the new partitions, ran the chkdsk with all options on to make sure the resulting partition survived the migration, then checked if it is readable under Linux (it was), used KPartitioner to grow the partition to the new size, again booted into Win7 Recovery, ran chkdsk with all options on, removed bootloader and made a new one using bcdboot.

Now, my Linuxes boot OK (there was some wankery involved but nothing too serious), but neither of my two Win7 can. I checked the bootloader, fiddled with different settings (e.g. removed setting the root by UUID), even tried to manually boot it from commandline - to no avail. After "chainloader +1" and "boot" it just does nothing. No error messages, nothing at all - the console screen doesn't even clear.

Any ideas?

---

### Post by srs5694 on 2010-03-13
Windows is *very* fussy about its boot partitions' start points. With recent versions, the only way I've successfully moved a Windows installation to a partition with a different start point than the original was using the [DriveImage XML](http://www.runtime.org/driveimage-xml.htm) backup software. Even then, the copy didn't boot immediately; I needed to use the Windows installation disc to restore it to bootability. (It did this more-or-less automatically when I ran it, as I recall.)

Therefore, my suggestion is for you to resize your Windows partitions, create fresh filesystems on them (using mkfs.ntfs in Linux or your original Windows installations), and copy the Windows installations with DriveImage XML or some other Windows utility that's designed for the job.

There may be some better way around this problem, but if so I haven't found it. Extensive Googling has turned up lots of forum posts and blogs about how Windows doesn't boot, and the solutions always seem long and complicated. The couple I tried didn't work for me.

---

### Post by Burillo on 2010-03-13
the problem is if i take your approach this would mean engaging in a whole lot of fiddling around with hard drives since i only got one 2.5" enclosure and three 2.5" HDD's (old one, new one and a backups drive) which i will have to swap around between enclosure and my laptop in order to even boot up to old OS. not to mention when i was finishing backup process i screwed something up (luckily, after i imaged two Win7 drives) with partitions and now the old Windows's won't boot too - meaning i will have to look out for my Win7 DVD to make them bootable again. If there is any other way to solve this problem other than restoring partitions from backup and reimaging them using another backup solution - i would reeeeeeeeeally like to know it...

---

