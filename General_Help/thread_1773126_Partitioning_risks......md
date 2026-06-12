---
title: "Partitioning risks....."
date: 2011-06-01
forum: General Help
---

### Post by iclestu on 2011-06-01
Having just had a bit of tussle trying to alter the partitions on my hard drive and having seen the standard 'partition table' warnings more times than I could possibly remember, I wondered what can go wrong and what the stats are?

I mean out of 1,000,000 partition attempts how many are likely to fail? How many result in a funked up hdd?

Just curious....

---

### Post by johngreth on 2011-06-01
I bet that only a few in every million partition operations result in an actual error.

That being said, it is very common for people to mess up settings and accidentally delete data that they intended to keep. That's the real reason why they put the warning there.

A while ago when I upgraded Ubuntu, I told it to use my old home folder, but it decided to use the old partition and write over the data instead. It was probably my fault and I didn't have a backup because I didn't care about the actual data on it, but I still pisses me off that it did that.

---

### Post by srs5694 on 2011-06-02
Although partition table data structures aren't that hard to manipulate, there are things that can go wrong, both with partitioning software and with related things (users, filesystem manipulations, etc.). Some specifics:


[list]
[*]TestDisk is known to occasionally create extended partitions that are *too* extended -- they're too big to fit on the disk. This is an illegal condition that causes some utilities (GNU Parted and GParted in particular) to flake out and claim that the disk is entirely unallocated.
[*]The Windows XP installer is known, under certain circumstances, to inappropriately convert logical partitions into primary partitions without adjusting the size of the extended partition. This causes GNU Parted and GParted to flake out much as in the previous case.
[*]The Windows 7 (and I think also Vista) installer is even worse; instead of converting logical to primary, it *deletes* partitions without prompting.
[*]I once caught OS X's Disk Utility deleting a partition it shouldn't have touched. I never investigated further, though.
[*]I've heard of, and once or twice witnessed myself, programs that delete some or all logical partitions when they get the data structures scrambled.
[*]If a disk is used as a GUID Partition Table (GPT) disk and then converted to Master Boot Record (MBR) form by a utility that doesn't understand GPT, there will be leftover GPT data on the disk. Although this technically makes the disk a valid MBR (not GPT) disk, some utilities (again, GNU Parted and GParted head the list) get confused by this condition and report the disk is empty. IIRC, Palimpsest uses the GPT data rather than the MBR data in this case.
 
[*]Some boot loaders try to support more than 4 primary partitions by keeping data on more than four partitions and then juggling them in and out of the partition table. There was a thread here recently that was started when somebody had problems because such a boot loader restored an old partition table that the Ubuntu installer had modified. The symptom was that partitions just seemed to vanish.
[*]Users can accidentally delete partitions, of course, as johngreth says. In fact, users can be very creative in their errors, particularly when they're dealing with unusual setups like [hybrid MBRs.](http://www.rodsbooks.com/gdisk/hybrid.html)
[*]When resizing or moving partitions and the filesystems they contain, the number of possible problems multiplies, since filesystem data structures are so much more complex than partition data structures. With data being moved around, a bug, hardware fault, or undetected corruption prior to the operation can easily result in everything flying out of control and serious loss of not just partition data but filesystem and file data.
[*]A power failure at an inopportune moment can trash data. This is especially true of filesystem resize/move operations, since they take so much longer than simple partition adjustments.
[/list]


The first few of those items are program bugs that I know of. In fact, they're common enough that I wrote a utility ([FixParts](http://www.rodsbooks.com/fixparts/)) specifically to fix them.

I have no idea what the frequency of errors is. The frequency might be as low as the "few in every million" figure that johngreth estimates, but only for actual bugs or write errors in *simple* operations such as writing a partition table with fdisk. Once you add in advanced partitioning operations (creating hybrid MBRs, recovering lost partitions, converting between partition types, etc.), operations involving filesystems, and user errors the problem rate must be *much* higher than that. Based on my own experience with partitions on my own computers and those I've partitioned for employers, I'd guess that somewhere between 1 in 10 and 1 in 100 operations goes bad in one way or another. Simple operations, like setting up an initial partition table, are unlikely to go wrong; but move/resize operations are particularly risky, and the more complex the setup, the more likely it is that something will go wrong.

---

