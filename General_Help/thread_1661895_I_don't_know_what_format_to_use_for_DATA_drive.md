---
title: "I don't know what format to use for DATA drive"
date: 2011-01-07
forum: General Help
---

### Post by CP2 on 2011-01-07
Hello all. So I built a new PC and I partitioned the Box as so:

Windows partition: NTFS
Ubuntu: Ext2
Not loaded yet, but will load OpenSUSE: Ext3
Swap: 10 GB
Then there is 650 GB Unallocated

I want to use this 650 GB as a data storage for the Ubuntu AND OpenSUSE. I'm not familiar with file systems when it comes to Linux, so what kind of file system should I format that 650 GB to?

---

### Post by KeyserSoze93 on 2011-01-07
I would use ext3.  If your drive every starts grinding and you need to rescue the data ASAP and you've only got a 5 year old rescue CD to hand, you'll be glad you can still read the filesystem with it.

Not that this has every happened to me, but it's not impossible!

---

### Post by seawolf167 on 2011-01-07
ext3 if you will only access it through a Linux-based OS, otherwise NTFS if you want access through Windows

---

### Post by CP2 on 2011-01-07
So what format would I install the 2nd Linux OS onto? Ext 3 as well?

---

### Post by artie_effim on 2011-01-07
What will you be using the 650GB partition for? Will it have loads or R/W operation on loads small files (<10KB)?  If so I'd go with XFS. Else I'd go with ext4 as a good catchall.  Stay away from ReiserFS as it is not being currently supported. 

so, XFS or ext4

also - 10GB swap it wayyy too big, but if you have that extra space, I guess it doesn't matter.

---

### Post by CP2 on 2011-01-07
> **artie_effim said:**
> What will you be using the 650GB partition for? Will it have loads or R/W operation on loads small files (<10KB)?  If so I'd go with XFS. Else I'd go with ext4 as a good catchall.  Stay away from ReiserFS as it is not being currently supported. 

so, XFS or ext4

also - 10GB swap it wayyy too big, but if you have that extra space, I guess it doesn't matter.

I'll be using the 650 GB for music, movies, and documents. Should I also keep application data here as well or should I keep that on the OS partitions?

---

