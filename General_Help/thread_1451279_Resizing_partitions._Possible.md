---
title: "Resizing partitions. Possible ?"
date: 2010-04-10
forum: General Help
---

### Post by Chahel on 2010-04-10
Hi

is this possible ? I have 3 partitions 2 different Linuxes on of which Ubuntu and one MS Windows. One of the partitions has come  too small. Can I resize all in safe way when plenty of empty space on one partition ? Help valued.

---

### Post by shade5 on 2010-04-10
Resizing a partition means always risk. Every guide tells you to make a back up of your important data before.

As far as I know it is possible to resize, but I never did it before. If your partion software has a function to resize it should be obviously possible. 

I have no professional knowledge about hdd structures, but I would make a complete new system. That way you make sure no data gets corrupted. And it is no bad idea to construct your system from time to time anew anyway.

Make sure to defrag before.

---

### Post by MooPi on 2010-04-10
Yes very possible, but as the previous poster stated there is a risk of data loss. Backup backup backup. I have found the Linux app "gparted" to be a great tool for resizing.

---

### Post by Tux118 on 2010-04-10
Well, it is very dangerous to resize partitions, so it is not reccomended, but if you absolutely have to, back up all important files to a flash drive, or a different storage device. Then go to system---> administration ---> partition editor 

From there you will be able to do whatever you need to do with your partitions. 

Good Luck

- Tux118

---

### Post by Chahel on 2010-04-10
Ok. Thanks for the warnings. I have decided to first burn all important things to dvd and then simply reformat and create the partitions i need.
I have seen people advice to make separate partitions for the base system and partitions for storage of files to easily update system. What is a good "strategy" for laying out partitions ? And are there any configuration files I might easily forget existence of before formatting ?

---

### Post by oldfred on 2010-04-10
It depends on how much data you have and what systems you have.

For new users just root & swap is all that is required since data use is not really known. If dual booting with windows then a shared NTFS partition can be useful for data you may want between systems.

If planning regular total reinstalls of Ubuntu then a separate /home becomes worthwhile.

But if using multiple Linux systems you should not share /home as software versions and settings may not be the same. But you can share all the data without any problems.

Some previous discussion:
[http://ubuntuforums.org/showthread.php?t=1443814](http://ubuntuforums.org/showthread.php?t=1443814)

How to Multi-boot (Maintain more then 2 OS) 2008 but good info
[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)
Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions of data linking from above blog, based on more from comments
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)
[http://ubuntuforums.org/showthread.php?t=1443814](http://ubuntuforums.org/showthread.php?t=1443814)

---

### Post by Chahel on 2010-04-10
Thank you for very useful links Oldfred. I consider my topic solved and this thread closed.

---

