---
title: "Can running the live CD affect my windows install?"
date: 2009-09-18
forum: General Help
---

### Post by enerj on 2009-09-18
I just installed windows and then ran the ubuntu live cd afterwards.  I may be imagining things but my windows install seems slower.  I did shrink the windows volume before running the live cd to make room for the linux partition.  Maybe this affected it?

Any possibility of this?

Thanks

---

### Post by bruno9779 on 2009-09-18
Before answering I must ask: Why did you partition your HDD to run LIVE CD ????????????

LIVE CD implies exactly that you can run it without installing anything.

On the other end, there is a chance that partitioning your HDD will decrease performance, for most filesystems. 
I have set up 10s of dualboots, without ever noticing any difference.

What HDD do you own? and how did you partition it? with which tool? what CPU and RAM do you own?

---

### Post by enerj on 2009-09-18
It's a WD 160gb 7200rpm sata drive.

I partitioned because I thought i was going to install.

I paritioned it with windows 7 disk manager.

I'm using a Q9550 quad core 2.83ghz cpu with 4 gigs ddr memory.

Thanks!

---

### Post by 3rdalbum on 2009-09-18
Ubuntu's installer can resize Windows partitions too, so you needn't have bothered with the Windows 7 disk manager, but no harm done.

Unless you run the Install program on the live CD and click OK on the screen where it asks you if you're really sure you want to change the partitioning, the live CD will not touch the Windows side of your disk. It won't even be mounted by default.

---

### Post by bruno9779 on 2009-09-18
I know you can test the performance of a linux filesystem using something like _[this]("http://www.cyberciti.biz/tips/how-fast-is-linux-sata-hard-disk.html")_

but i don't know if it will work on the Live CD and I don't think it will with NTFS

---

