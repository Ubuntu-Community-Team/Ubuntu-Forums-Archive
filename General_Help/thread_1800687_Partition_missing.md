---
title: "Partition missing"
date: 2011-07-09
forum: General Help
---

### Post by fourteen on 2011-07-09
It's the first time I've installed ubuntu, because I have two computers and I don't think having Windows on both of them is something interesting. So I formatted my Compaq Presario and installed ubuntul from scratch.

As you probably figured it out, a partition is missing from My Computer. The partition is quite big as well, around 110GB, while the one I have is only around 50GB.

So please, any **tips for a beginner**?

---

### Post by leclerc65 on 2011-07-09
I use Gparted or better still, Parted Magic (which contains Gparted and more) to handle partitions.Just Google for them.

---

### Post by An Sanct on 2011-07-09
> **fourteen said:**
> It's the first time I've installed ubuntu, because I have two computers and I don't think having Windows on both of them is something interesting. So I formatted my Compaq Presario and installed ubuntul from scratch.

As you probably figured it out, a partition is missing from My Computer. The partition is quite big as well, around 110GB, while the one I have is only around 50GB.

So please, any **tips for a beginner**?

If you wanted a full install to a computer (no dualboot option) then simply insert the CD and follow the instructions :) The installation will take care of any formatting process needed.

---

### Post by ajgreeny on 2011-07-09
I do not understand what you mean by "a partition is missing"  Can you explain more, or better run gparted from you installed ubuntu, or a live CD if necessary, and post a screenshot of what it finds back here.

---

### Post by Wim Sturkenboom on 2011-07-09
In a terminal, run sudo fdisk -l (that is, lowercase L) and post the output here between [noparse]```
 and 
```[/noparse]

Example from my netbook (command in bold)
```

wim@aa0:~$ **sudo fdisk -l**
[sudo] password for wim: 

Disk /dev/sda: 8069 MB, 8069677056 bytes
255 heads, 63 sectors/track, 981 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003255d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         918     7367680   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2             918         981      509953    5  Extended
Partition 2 does not end on cylinder boundary.
/dev/sda5             918         981      509952   82  Linux swap / Solaris
wim@aa0:~$ 

```

---

