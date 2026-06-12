---
title: "What ever happened to Use Largest Continous Free Space?"
date: 2011-01-08
forum: General Help
---

### Post by zacharyh on 2011-01-08
After a terrible problem I had with x-server, I decided to opt for a clean install.

So, naturally I poped in the 10.10 LiveCD (from Canonical), deleted the Ubuntu Partiton (ext4) and swap, and entered the installer. I have a 40gb Vista partition, 90gb media partition, and 20gb unallocated free space.

Once I get to allocate drive space in the installation, I get three options - Install alongside other operating systems, erase and use the entire disk, or specify partitions manually. If I click install alongside other operation systems, it tries to take space away from my media partition to install ubuntu. 

I'm not too advanced with Ubuntu, so I don't think I'm going to specify my own. I don't know how much to give swap etc, etc, etc.

What ever happened to use the largest amount of continuous free space? I have 20gb free I would love ubuntu to use.

Any suggestions?

---

### Post by Verbeck on 2011-01-08
> **zacharyh said:**
> 
What ever happened to use the largest amount of continuous free space? 

not sure whether it's included in the 10.10 installer
(read that they removed the feature)

> **zacharyh said:**
> 
Any suggestions?

select manually partition and create the partitions as follows;
.:swap:.
type=swap
size=same as ram

.:filesystem root:.
type=ext4
size=the rest (or if you want a separate /home, 10gb would do)
mount point= /

.:home:. (optional. would save the files in your home directory if you need re reinstall the OS again)
type=ext4
size=the rest after you've set up the previous / partition
mount point= /home

hope that helps

---

### Post by zacharyh on 2011-01-08
> not sure whether it's included in the 10.10 installer
(read that they removed the feature)

Must have, what a shame (well to me anyways)

I think a separate home would be good for me, in case I have to reinstall again I don't have to lose everything.

Thanks for the tips!

---

