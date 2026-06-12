---
title: "Need to partition my External Hard drive without Losing Data"
date: 2011-10-17
forum: General Help
---

### Post by mac4rfree on 2011-10-17
Hi guys,
 
I have an External Harddrive 500 GB. It contains 300 GB of data. I do not want to lose the data.
 
But the problem is drive is in FAT32 format. But i need to store a 5 GB file. So, i want to create a partition of 100 GB so that i can format it in another format.
 
So, can somebody guide me as how to partition the harddrive without losing the data and also which tool to use for it (gparted???? )
 
Cheers!!!!

---

### Post by Mark Phelps on 2011-10-17
My own experience has been that MS Windows partitioning apps work best on MS Windows filesystems; Linux partitioning apps (e.g., GParted) work best on Linux filesystems.

My advice would be to do the following:
1) Plugin the external drive to an MS Windows PC
2) Download and install Partition Wizard (which is FREE) on the Windows PC
3) Use Partition Wizard to make the changes.

You can also use EASEUS Partition Master (which is also FREE), if you prefer to use that.

---

### Post by Slim Odds on 2011-10-17
gpartd works just fine for FAT32 partitions (and just about another other types that it supports).

Just make sure that you BACKUP first. Always BACKUP first.

---

### Post by mac4rfree on 2011-10-18
Guys, i thought of giving a shot at gparted yesterday. It was a easy cake walk.
 
And data is unharmed. :)

---

