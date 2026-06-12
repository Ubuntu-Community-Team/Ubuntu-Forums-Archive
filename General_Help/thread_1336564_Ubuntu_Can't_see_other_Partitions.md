---
title: "Ubuntu Can't see other Partitions"
date: 2009-11-24
forum: General Help
---

### Post by Engromada on 2009-11-24
Ubuntu Can't see other Partitions on my main hard drive, and i kinda need it to :tongue:

I used cfdisk to divide the disk like this:


[LIST]
[*]*sda1 ext2 100GB (slackware installed)*
[*]*sda2 ext2 100GB (ubuntu installed)*
[*]*sda5 swap 2GB*
[*]*sda6 ext2 50GB (for playing with different distros)*
[*]*sda7 FAT32 (rest of disk, my main file storage, for personal files)*
[/LIST]

It's sda7 i mainly want access to, i already have access to my slackware partition.
sda7 has not been touched since i created it with cfdisk when i bought the new hard dirve and ubuntu and slackware are pretty much fresh installs.  my hard drive is SATA.

*hopes there is a simple solution to this*

Engromada.

---

### Post by Engromada on 2009-11-24
i just answered my own problem!

drive wasn't formatted! how silly.

---

