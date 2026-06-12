---
title: "Question on Partitioning - can I increase a partition?"
date: 2010-09-14
forum: General Help
---

### Post by listerdl on 2010-09-14
Hi - using GParted, this is how my partitions look:

Unallocated: 101.98 MB
[COLOR="DarkOrange"]/dev/sda1: NTFS - 19.53 GIG * This has Windows 7[/COLOR]
/dev/sda2: ext4 - 19.53 GIG * This has Ubuntu
/dev/sda3: linux-swap 0 MB * This seems to do nothing
/dev/sda4: NTFS - 107.70 GIG * This has shared Hosting

----------------

My question is, my space in the orange font color, Windows, has very little space left. If I increase this partition, will it have a negative knock on effect to the rest of the partitions?

I know that I can use clonezilla and restore if things to wrong but do you think it will be ok?

Thanks!

---

### Post by d5xtgr on 2010-09-14
I am by no means an expert, but I recently did something similar- for me at least, gPartEd moved files around (this took about 2 hrs) and then reformatted a chunk of the 'unallocated' space without problems.  From what I understand, that space can't be used until the computer knows what to look for (as in at least a filesystem) so your unallocated chunk isn't doing anything.  Also, unless you have a lot of RAM, your swap space is normally recommended to be twice your RAM space.

---

