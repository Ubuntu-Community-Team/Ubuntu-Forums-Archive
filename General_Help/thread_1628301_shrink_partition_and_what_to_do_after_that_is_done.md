---
title: "shrink partition and what to do after that is done"
date: 2010-11-22
forum: General Help
---

### Post by toolmania1 on 2010-11-22
[FONT=Calibri]So I have read up onsome partitioning.  I have a questionthat I have not seen the answer to ( although I am sure it is here somewhere).  I have not tried anything yet, butlater I am going to try to shrink my main partition.  I want to have a separate partition to storedata and backups.  I only have a 40GBhard drive, so I know I am limited already. However, Ubuntu does not seem to hog space like Windows XP did with allits updates.  [/FONT]
[FONT=Calibri]Anyways, if I rungparted, and shrink the main parition to lets say around 30 GB.  I know there is already, or should be, a swappartition.  So, that would leave between9 and 10 GB.  [/FONT]
[FONT=Calibri] [/FONT]
[FONT=Calibri]My first questionis:  Is that enough space?  I know it is dependent on what I do.  We want to at least temporarily save photosand movies until we can get them onto cd / dvd. They usually do not stay longer than a month without going onto sometype of permanent storage like a cd or dvd. [/FONT]
[FONT=Calibri] [/FONT]
[FONT=Calibri]Second, do you haveto format the second partition or something else once I shrink the firstpartition?  How is that done?[/FONT]

---

### Post by ajgreeny on 2010-11-22
1.  Why do you say there is already a swap partition?  Windows does not use the same system for its "virtual memory" or swap as linux does, so if you have not made a swap partition there will not be one to use.  You will therefore need to allow for that to be made at install.

2.  You must make sure you defrag your windows partition a couple of times before you shrink it, or you may not be able to shrink it as far as you would like.

3.  You can shrink it with gparted when you run the live CD for the install, which is probably the best way for XP, but make sure you make the free space at the end of XP; do not attempt to move the start point of XP to the right in order to put ubuntu at the start of the disk, or you could have problems.

4.  10GB is very small if you want to put movies and photos on there.  A normal DVD movie is about 4.7GB, though it can be shrunk with the right software.

5.  When you get to the partitioning stage of the install, assuming you have made the free space already, choose manual partitioning, and there make a new 9GB ext4 for root, and a 1GB for swap.  That should be the best with such limited space available.

---

### Post by toolmania1 on 2010-11-22
Sorry, I mislead you.  I wiped my hard drive and clean installed Ubuntu.  I want to shrink the main Ubuntu partition.  Then, add a partition with the leftover space.

---

### Post by bonixavier on 2010-11-22
1-20GBs are more than enough for the system install. Maverick installed around 7GB of data here. I'd recommend you to keep most of the room for a /home partition as it will allow you to keep your settings if you have to reinstall, upgrade or change distro. (Sometimes there are incompatibilities between distros, but all your files are there).

2- Yes, you have to format the second partition. mkfs.ext4 /dev/sda3 (for example).

3- After that, you'll have to assign a mount point for that partition and transfer the files you want to it.

---

