---
title: "Installing Ubuntu"
date: 2011-02-01
forum: General Help
---

### Post by vlad951 on 2011-02-01
Hello everyone.

So I've finally decided to install Ubuntu, and remove Windows 7. I currently have three partitions. One is a 200MB partition reserved for Windows 7, there's another C:\ partition (80GB) on which the operating system is installed and D:\ (350GB) is where all my data resides (music, movies, etc). Now I have two questions:

1) If I remove the first two partitions, the 200MB one and C:\, will the D:\ partition be left intact and still work?

2) What partitions do I need to create for Ubuntu? Or maybe I should let the installer to do it automatically for me with the optimal settings and sizes of the partitions? (There will be about 80GB for Ubuntu).

---

### Post by vlad951 on 2011-02-01
Bump.

---

### Post by fret669 on 2011-02-01
Gparted should show you the status of all three of your partitions, so as you delete them, you'll be able to tell. Nothing happens to your hard drive until you hit next, after customizing your disk layout in my experience.

Bare minimum, you just need one partition for Ubuntu. I personally have one "/", "/home", and "swap". If you'll be using your D: partition, you won't really need a /home partition. A "swap" partition is a good idea though. 

If you have 80gb to work with, and you aren't making a home partition, just make the swap partition the same size as your ram. You can give ubuntu the rest, or if you want to make a separate /home partition, you might want to give ubuntu at least 8gb for itself.

---

### Post by oldfred on 2011-02-01
The auto installer does not create an optimal install, just a default that will work. You have to manually create partitons if you want full control. And the latest version is easy to use the wrong button and end up installing to the full drive or partition or what it actually does is erase drive. I strongly suggest partitioning in advance.

Issues:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
From kansasnoob:
[http://ubuntuforums.org/showpost.php?p=10145206&postcount=15](http://ubuntuforums.org/showpost.php?p=10145206&postcount=15)
Trust me here! If you choose either "Use entire partition" or "Use entire disc" you are not likely to end up with "Alongside" anything! You will most likely lose the OS and any data contained therein!

Installs:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Installing Ubuntu in Hard Disk Two (or more) internal or external
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)

My standard suggestion, adjust as needed:
For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

### Post by vlad951 on 2011-02-01
OK, thanks for your help.

Do you think the following partitioning scheme is fine?
/ - 20GB (Primary, beginning).
/home - 56GB (Logical, beginning).
Swap file - 4GB (Logical) - I have 4GB of RAM.

Another question, is there anyway to convert that D:\ partition into ext4?
Because I don't have a backup drive to back up all that data that is on that drive, then erase everything and create a new ext4 partition...

---

### Post by oldfred on 2011-02-01
Partitioning is fine. Everyone has different needs and even what is optimal today changes tomorrow.

No, you cannot convert from NTFS to any other format without erasing all the data. You should have some backup. DVDs, CDs, flash drives or some external device. 

It will work ok as NTFS, I still have my shared NTFS partition as I still occasionally boot XP. You should download a win repair disk and run chkdsk every 50 reboots or if you have troubles. Linux can only do minor repairs to NTFS, or with testdisk sometimes repairs chkdsk cannot do.

Windows 7 Disc - for repairs only
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista/7 will not auto repair XP (they create the boot sectors differently) but can run chkdsk on any NTFS partition.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

