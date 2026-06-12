---
title: "ext2 to fat32"
date: 2010-02-13
forum: General Help
---

### Post by pooper on 2010-02-13
Hi all, 

just need some advice..

I have a maxtor external hd of 1tb, at the moment it has partitions 30gb fat32 and the rest ext2 however I now want to convert the whole lot to fat32 so it is compatible across various machines such as my ps3 and apple..

My problem is I have data on both partitions I want to keep, but do not have room to store temporarily whilst I do the conversions. So I was wondering is it possible to achieve this conversion with the data there without sacrificing it?

---

### Post by tom4everitt on 2010-02-13
There's no way to "just convert" an ext2 file system to a fat32 (they're too different). Basically the only file systems you can convert between is ext2, ext3 and ext4. 

If you have a lot of time you can shrink your ext2, extend the fat, move some files, shrink ext2 again, grow fat, move some files again etc. If you have more than half the drive free this could be an option. Shrinking and growing file systems is quite time consuming though. 

Also, don't forget that fat32 systems can't store files bigger than 4gb.

---

### Post by pooper on 2010-02-14
ok thanks, just wanted to clear that up that there is no way to convert file systems. I managed to move the files about onto various other storage, then changed to fat32 then moved back files. 
I'm aware can't have files over 4gb not a problem at the moment. However fat32 is the only cross compatible file system it seems..

---

