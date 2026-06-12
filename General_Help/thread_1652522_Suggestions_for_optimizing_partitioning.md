---
title: "Suggestions for optimizing partitioning"
date: 2010-12-25
forum: General Help
---

### Post by Telos3K on 2010-12-25
In migrating from wubi to a dual boot set up, I of course had to set up partitions but didn't quite know what I was doing despite having read HowToPartition, etc.  I've since deleted the ones I didn't need and resized others, but it's still not a very efficient set up. I'd welcome any suggestions from partitioning gurus on how to improve this (that can be safely accomplished by a relative newcomer).  I've attached a screenshot of the GParted screen.

[LIST]
[*]sda1 is the Windows recovery partition
[*]sda2 is the Windows OS (C drive) -- I shrunk this via Windows Disk Management window as far as it was suggested
[*]Then, a 52GB unallocated block
[*]sda5, which is my Windows D: drive and my Ubuntu DATA drive. Obviously I want to maximize the size
[*]sda6, where my Ubuntu OS files are
[*]sda7, a 5GB swap partition.
[/LIST]

My thought was to move sda6 over to the right up against sda7 and then expand sda5, but GParted warned against moving the start of the partition with the boot directory.  And that would still leave that 52GB unallocated block......

Also, is there a best practice on leaving a buffer between partitions?

Many thanks.

---

### Post by ridgeland on 2010-12-27
Comments from a non-guru.
You can have 15 partitions (maybe 16 but I've had trouble with 16 so I stop at 15).
I always keep at least 3 partitions of 10 GB to install Linux systems.  Don't keep data in /home/my/mydata.  Keep all your data in /Data partition(s).
I've never heard anyone want gaps of unallocated!
I would use:
sda 1 as is
sda 2 as is Windows
sda 3 as Windows D: - only data that Windows must have
   (Linux will be able to read/write to it)
sda 4 - extended partition all the rest
   (sda5, etc are part of this extended partition)
sda 5 - linux swap - I use 4 GB
sda 6 - linux only data - things windows will not use
sda 7 sda 8 sda 9 all Linux operating system - 10 GB each
The reason for three is - one to use - one for a clone copy of the one you use - for a sandbox or recovery if you crash the main one and the third for trying the next release without letting go of the current release.
I use ext3 but most prefer ext4 for the Linux partitions. ntfs for Windows.  Grub can list dozens of boot options of kernel versions, partitions etc.  I have Fedora, SuSE and Mandriva besides a few copies of Ubuntu.

---

### Post by piquat on 2010-12-27
> **ridgeland said:**
> I've never heard anyone want gaps of unallocated!

I *think* the reasoning is to put the OS's at the outside of the disk, where the disk is spinning faster, relative to the heads.  Then you put a storage partition at the end of the scheme so it's ends up on the inside of the disk, near the spindle.  Then you leave that unalocated space there in case you want to install another OS.

---

