---
title: "merging 2 partitions of HDD"
date: 2011-05-25
forum: General Help
---

### Post by thexnightmare on 2011-05-25
Dear,
I have 2 partitions on my 50 GB HDD.
1st 20GB (ubuntu), 2nd 30 GB (Data).
I want to merge data partition to the first one.
How can I do that?
Thx

---

### Post by seawolf167 on 2011-05-25
You'll want to boot off an Ubuntu LiveCD or GParted LiveCD, then once booted, use the GParted "merge" option to merge the partitions together.

Alternatively, (and IMO better), create a separate /home partition following [this guide]("https://help.ubuntu.com/community/Partitioning/Home/Moving"), then merge the Data partition with your /home partition

That, or you could simply add an /etc/fstab entry to automount your Data partition upon boot, then just leave it as a separate partition

---

### Post by thexnightmare on 2011-05-25
Dear,
I just booted with ubuntu live cd and i am in gparted now, but dont see merge option!!!???

---

### Post by seawolf167 on 2011-05-25
I thought it did - oh well, its not that big a deal, you can copy the contents of your data partition to an external drive for temporary storage or write the contents directly to your Ubuntu partition. Once your contents have been moved, you can delete the data partition and resize the Ubuntu partition. Here is an [older ]("http://gparted.sourceforge.net/larry/resize/resizing.htm")how-to with pictures (you'll have a different format type [ext3 or ext4]), some of the images may be a little different.

---

### Post by thexnightmare on 2011-05-25
This worked very good with partitions but not the main partition where ubuntu is installed.
Main partition cant be resised to get other partition space.
Note: the partition is empty.

---

### Post by seawolf167 on 2011-05-25
Are you running from within a LiveCD? In order to resize / you cannot have it mounted

---

### Post by thexnightmare on 2011-05-25
Yes i am running from live cd and it is unmounted

---

### Post by seawolf167 on 2011-05-25
Has your data partition (the empty one), been deleted (i.e. shows as unallocated space)?

---

### Post by LordNeo on 2011-05-25
Check the swap partition, it gets automounted and it doesn't allow to resize the extended partition

---

### Post by thexnightmare on 2011-05-25
LordNeo, you are right, I deleted it and now everything is ok. thx.
Just a question, do I need to recreate a swap partition, and how much size do u prefer?

---

### Post by LordNeo on 2011-05-25
Well, you didn't had to delete it, just to unmount it xD
Anyway, anything from 1gb to 2gb is ok, i've never used it (i have 4gb ram) so, let it be 1gb and check how it goes

---

### Post by thexnightmare on 2011-05-25
I have 4gb too.

---

### Post by srs5694 on 2011-05-25
If you expect to use the suspend-to-disk feature, your swap partition *must* be at least as large as your RAM size. Thus, it's best to go at least a bit larger than your RAM (to allow for rounding errors and GB vs. GiB confusions) -- say, 1.2x your RAM size. If you don't expect to use the suspend-to-disk feature then this isn't critical, but IMHO it's still best to create a swap partition of this size in case your needs change in the future. (The disk space required is small compared to modern hard disk sizes.) In the past, having swap be at least twice your RAM size was recommended, but for most users of modern computers, that's bordering on overkill.

---

