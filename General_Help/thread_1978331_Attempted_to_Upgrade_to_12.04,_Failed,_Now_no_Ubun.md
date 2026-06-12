---
title: "Attempted to Upgrade to 12.04, Failed, Now no Ubuntu"
date: 2012-05-11
forum: General Help
---

### Post by guyfromfl on 2012-05-11
I am trying to migrate from 11.10 to 12.04, but ran into a problem.  I am upgrading from the installation disc but when I tried, I got an error that said "Unable to unmount partition System Reserved..."(at least something along those lines) I exited the installer, and tried to boot back into ubuntu. after the grub it flashes some error message that flashes about as fast as a subliminal message, then just a black screen.  I let it sit for about 10 minutes and nothing happened.

I was watching the msgs in the installer, and didn't see anything that would have disrupted the partitions, it didn't get that far.  I think the last msg it showed before the error was "Analyzing Drives" (again along those lines..)

Now Windows does not see the 2 partitions, home and the one I used for data storage, but the windows disk manager does.  I have them backed up and currently ghosting the entire physical disk.

The Partition that Ubuntu installer did not like is called "System Reserved"  I tried to boot into the live CD, unmount then install but it would not let me.

Does anybody have any suggestions on how to get this back up and running?

I tried this exact procedure on 2 other upgrades without any problems.

---

### Post by guyfromfl on 2012-05-11
Does anybody have any suggestions?

---

### Post by Oscailt on 2012-05-11
I'd say the best option would be to format said partition using a LiveCD of GParted. Then do a fresh install of Ubuntu 12.04 on they newly formated partition.

---

### Post by nidzo732 on 2012-05-11
DON'T touch that patition, Windows needs it.

---

### Post by Mark Phelps on 2012-05-11
You haven't provided enough info other than to have us advise to leave things alone!

To get a better look, boot from an Ubuntu LiveCD, open a terminal, and enter the command "sudi fdisk -lu" (lowercase L, not a one).

That will list out the partitions on your drive and give a better idea of what you have in place now.

Do NOT touch the System Reserved partition -- period!

---

### Post by guyfromfl on 2012-05-13
Thanks for the feedback. I know just enough about this stuff to ruin things lol. 

I don't understand why the installer will not continue with that mounted, if its not supposed to be there...

here is the result of sudo fdisk -lu:
```

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4c0df721

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   205006847   102400000    7  HPFS/NTFS/exFAT
/dev/sda3       205008894   307406847    51198977    5  Extended
/dev/sda4       307406848   561313097   126953125   83  Linux
/dev/sda5       205008896   266874879    30932992   83  Linux
/dev/sda6       266876928   307406847    20264960   83  Linux

Disk /dev/sdb: 4009 MB, 4009754624 bytes
145 heads, 48 sectors/track, 1125 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes


```

sda2 is windows7 pro
sda4 is my data storage where the database tables were stored
sda5 is where ubuntu was originally
sda6 is my home partition

Thanks for the help

---

