---
title: "partitioning and swap partitions"
date: 2009-12-04
forum: General Help
---

### Post by dln9 on 2009-12-04
I  am running Ubuntu 9.10.  

I just recently completed installing Ubuntu 9.10, and abandoning Windows XP.  I spent the past week or so getting everything set up and working, finding all the packages needed to do stuff, etc.  

Before partitioning the drives - I have two of them - I had read that a general guide is to make the swap partition equal to 50% - 200% of the RAM.  Since the RAM is 1 GB, I decided to make the swap partitions equal to 2 GB - 1 GB on each drive.  

Yesterday I was just reviewing things, and I ran the application that shows how information about the various drives (I forget what it is called).  I saw to my dismay that when I was setting up the partitions I must have typed in too many zeros, because I have 10 GB set aside on each drive for the swap partitions.  So, I am wasting 18 GB - 9 GB on each drive.  

I would like to recover those 18 GB, and add them to the partitions on each drive for the operating system, HOME folders and files, etc.  I don't know how to do what without ruining all the work I've already done to set up Ubuntu.  

Anyone know of approach that will work in this situation?

---

### Post by audiomick on 2009-12-04
hallo.
If you boot from the live CD, you can run gparted from there (system> administration> gparted) and move things around. If you have any data on the computer already, back it up first. A good thing is to archive out your /home folder, if you have enough space somewhere externally.

As long as you think carefully about what you are doing, you shouldn't have problems.

---

