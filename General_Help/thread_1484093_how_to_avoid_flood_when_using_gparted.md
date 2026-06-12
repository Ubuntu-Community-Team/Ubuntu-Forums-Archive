---
title: "how to avoid flood when using gparted"
date: 2010-05-15
forum: General Help
---

### Post by monkeybean on 2010-05-15
hello! im a total noob so i will just post anything i think might be important to know.

specs: toshiba lappy
110gb hdd, 1gb ram, core 2 duo 1.6ghz, nvidia 7600
windows xp pro service pack 3
jaunty jackalope


my problem is: i wanted to repartition (shrink xp and create partition for data storage) my hdd using gparted live cd 0.5.2-9. everything went fine until i clicked exit and reboot. after the cd tray automatically ejected i got a flood of "VFS: busy  inodes on changed media or resized disk srO". this doesnt stop until i press enter. after that it reboots normally and there is  no problem with the os.

my questions:
1) is that flood anything bad, is there a way to avoid this. i read somewhere that the problem is solved when using the  terminal sudo eject - then push back the cd tray - then sudo eject -t. i tried that but it said failed because gparted cd is in  use.

2) the first time that happened i didnt know what to do, so it flooded like for 15min or more until i pressed enter. my  question is if the flood is being saved anywhere on the pc so that i have to delete it?

and a question regarding extended partition:
3) i have 50gb left that i want to use for data storage. i read that you can only have one extended partition. so since there is  already one extended partition from ubuntu, i cant have another one  for windows? so i can only make the data partition as  primary or is there another reason why the "create extended partition" is greyed out?

last question:
4) when i set up the partition for swap i made it 1032gb big but in gparted it shows 980.53mb. is that still enough or why is  it like that because somehow the sizes of the partitions seem a bit different than how they originally should be. im actually used in seeing the size shrinking a bit but i found it weird that the ubuntu partition shows 4.76 when it should be 4.5gb. i know its  not much different but im just curious to know why..


partitions order:
windows - unallocated (-->data partition) - ubuntu (primary) - home folder (extended) - swap

in windows the partitions are shown as:
windows xp (31,74gb) - unallocated (50,05gb) - 4,76gb unkown - 24,27gb unkown - 981mb uknown

in gparted: its almost the same, only difference: there is unallocated space (7 or 8mb) between home folder and swap


oky thats all, sorry if i asked too much but i couldnt find much googling so i thought of asking directly. im very thankful for any answers!

---

### Post by srs5694 on 2010-05-15
> **monkeybean said:**
> everything went fine until i clicked exit and reboot. after the cd tray automatically ejected i got a flood of "VFS: busy  inodes on changed media or resized disk srO". this doesnt stop until i press enter. after that it reboots normally and there is  no problem with the os.

/dev/sr0 is another name for your CD/DVD drive. Thus, the "busy inodes" mentioned in the error are on a read-only medium, and the problems are therefore non-permanent.

> 2) the first time that happened i didnt know what to do, so it flooded like for 15min or more until i pressed enter. my  question is if the flood is being saved anywhere on the pc so that i have to delete it?

If you booted from the CD/DVD, chances are this isn't being logged in any permanent way. If you booted from the hard disk, there may be records of it in a log file in /var/log; however, such records *should* be rotated out of existence in time. (There are things that can interfere with log file rotation, though, including shutting down the computer at night.)

> 3) i have 50gb left that i want to use for data storage. i read that you can only have one extended partition. so since there is  already one extended partition from ubuntu, i cant have another one  for windows? so i can only make the data partition as  primary or is there another reason why the "create extended partition" is greyed out?

Extended partitions are not "owned" by a single OS; there's absolutely no reason you can't add a Windows partition to an extended partition that currently contains nothing but Linux partitions.

> 4) when i set up the partition for swap i made it 1032gb big but in gparted it shows 980.53mb. is that still enough or why is  it like that because somehow the sizes of the partitions seem a bit different than how they originally should be. im actually used in seeing the size shrinking a bit but i found it weird that the ubuntu partition shows 4.76 when it should be 4.5gb. i know its  not much different but im just curious to know why..

I'll assume you meant "1032MB," not "1032gb," above -- a 1032GB (roughly 1TB) swap partition is ridiculously excessive! What you're running into is probably a difference between megabytes (MB; 10^6 bytes) and mebibytes (MiB; 2^20 bytes). Ironically, the normally precise computer industry often uses the megabyte (MB) term or abbreviation when it should be using mebibytes (MiB). In fact, this practice is so common that it's more of a "standard" than the technically correct terminology. This issue has been plaguing us for decades.

---

### Post by BoneKracker on 2010-05-15
I can't answer 1 and 2.

[QUOTE=monkeybean]and a question regarding extended partition:
3) i have 50gb left that i want to use for data storage. i read that you can only have one extended partition. so since there is  already one extended partition from ubuntu, i cant have another one  for windows? so i can only make the data partition as  primary or is there another reason why the "create extended partition" is greyed out?[/quote]

On a MS-DOS-style disk (which is what you have), you can only have four primary partitions.  One (and only one) of these primary partitions can optionally be an "extended partition".

However, that extended partition can hold one or more "logical partitions".  As far as an operating system goes, a partition is a partition -- it doesn't matter if it's "extended" or "logical".

You can create additional logical partitions, as long as there is free space inside your extended partition.  Also, as long as there is free space inside your extended partition, you can increase the size of one or more existing logical partitions.

Your extended partition is not "from Ubuntu".  Your extended partition is not dedicated to any particular operating system.  It is just a "container" for one or more logical partitions, each of which will be "formatted" with a particular filesystem (and therefore, probably dedicated to a particular operating system).  Any new logical partition you create can be used however you like (linux, windows, swap, whatever). You will choose a filesystem to put on the partition depending on how you intend to use it (e.g. ext4 for linux, ntfs for windows, etc.).

You said you have 50 GB free space.  If that space is adjacent to the extended partition, then you can expand your extended partition to include it.  Then you can either increase the size of a logical partion, or make a new logical partition.  Making a new one is less error-prone than expanding an existing one.

[QUOTE=monkeybean]
last question:
4) when i set up the partition for swap i made it 1032gb big but in gparted it shows 980.53mb. is that still enough or why is  it like that because somehow the sizes of the partitions seem a bit different than how they originally should be. im actually used in seeing the size shrinking a bit but i found it weird that the ubuntu partition shows 4.76 when it should be 4.5gb. i know its  not much different but im just curious to know why..[/QUOTE]
Depending on the tool you are looking at, it may be showing MB or MiB.  The correct unit for data, for most purposes is MiB (KiB, MiB, GiB, etc.). These are multiples of 1024 of the previous unit (1024 MiB in a GiB).  However, because they want to screw you, disk manufacturers have chosen to the SI definition of "kilo", "mega", and "giga" (multiples of 1,000).  So depending on which units are being used, the numbers may not match.

[http://en.wikipedia.org/wiki/Mebibyte](http://en.wikipedia.org/wiki/Mebibyte)

Also, tools may round off units for display.  And, partitioning tools may estimate the size (or you may "request" a certain size), but when the operating is being carried out, the boundaries between the partitions may be moved slightly to align with disk sectors.  This prevents wasting little bits of space between partitions.

For all those reasons, the numbers might be slightly different than what you expect.

[QUOTE=monkeybean]
partitions order:
windows - unallocated (-->data partition) - ubuntu (primary) - home folder (extended) - swap[/QUOTE]
Okay, so since your unallocated space is not adjacent to your extended partition, you can't simply add it to the extended partition.

You could move your ubuntu partition to push the unallocated space to be adjacent to the extended partition, but this can be hazardous and result in data loss.

It's not clear to me from your list whether the swap is a logical partition or a primary partition.  If it's a primary partition, then you have used all four partitions.  If that's the case, this is what you should do:

1. delete the swap partition
2. expand the extended partition
3. create a new logical partition to hold the swap space
4. make swap filesystem on that new logical partition

This would then leave you with 3 primary partitions:
- windows
- ubuntu
- extended
---- home
---- swap

Then, you could create a new primary partition from you unallocated space, and use is at a data directory (mount it to a directory inside your home directory or something)
- windows
- data
- ubuntu
- extended
---- home
---- swap

And that's probably the best course of action.

In any case, if you start moving or resizing partitions, be sure to back up your stuff.

---

### Post by monkeybean on 2010-05-15
thx alot srs5694 and bonekracker for taking your time clearing things  up! :)

@srs5694: oops, yup i meant 1032mb

@bonekracker: the swap is a logical partition


now there is one more i thing i would like to ask regarding this

> **BoneKracker said:**
> 

Your extended partition is not "from Ubuntu".  Your extended partition  is not dedicated to any particular operating system.  It is just a  "container" for one or more logical partitions, each of which will be  "formatted" with a particular filesystem (and therefore, probably  dedicated to a particular operating system).  Any new logical partition  you create can be used however you like (linux, windows, swap,  whatever). You will choose a filesystem to put on the partition  depending on how you intend to use it (e.g. ext4 for linux, ntfs for  windows, etc.).



if i understood correctly, it means if i were to move the unallocated  space and merge it with the extended partition, i could create a logical  one from the free space and format it with ntfs which would mean that i  could access this logical partition from windows even though the  logical partition is not adjacent to windows?

---

### Post by BoneKracker on 2010-05-15
[QUOTE=monkeybean]now there is one more i thing i would like to ask regarding this

if i understood correctly, it means if i were to move the unallocated  space and merge it with the extended partition, i could create a logical  one from the free space and format it with ntfs which would mean that i  could access this logical partition from windows even though the  logical partition is not adjacent to windows?[/QUOTE]

Yes, that is correct.

However, it would be much less of a problem to do what I said.  _Delete the swap partition, increase the the size of the extended partition by that much, create a new swap partition (logical) inside the extended partition.  Then just create a primary partition in the unallocated space between Windows and Ubuntu. Then put ntfs on that new primary "data" partition._  You would then be able to mount that data partition in both Windows and Linux.

Why is that better than "moving the unallocated space"?  Because you wouldn't really be "moving the unallocated space"; you'd be moving the whole ubuntu partition _into_ the unallocated space (and risking butchery of that data in the process).  You'd probably also have to move the extended partition into the space freed up by having moved the ubuntu partition (risking butchery of the data in your home directory). In addition to being risky, moving partitions is time-consuming.

---

### Post by monkeybean on 2010-05-16
> **BoneKracker said:**
> Yes, that is correct.

However, it would be much less of a problem to do what I said.  _Delete the swap partition, increase the the size of the extended partition by that much, create a new swap partition (logical) inside the extended partition.  Then just create a primary partition in the unallocated space between Windows and Ubuntu. Then put ntfs on that new primary "data" partition._  You would then be able to mount that data partition in both Windows and Linux.




i was actually planning to do what you suggested there, just wanted to know if i understood correctly^^ thx again for answering!

*edit*

how do i mark the thread as solved?

---

### Post by dcstar on 2010-05-16
> **monkeybean said:**
> 
........
how do i mark the thread as solved?

By using the Thread Tools.

---

