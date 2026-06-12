---
title: "Seting Up Multiple Hard Drives"
date: 2011-07-13
forum: General Help
---

### Post by slotdoctor on 2011-07-13
Hello everyone.

I am thinking of building a new computer. I have been using Ubuntu for a couple years now, but I am not  good with the terminal usage. Nevertheless, if I was to go back to Windows I be lost. My Computer would be:

Motherboard = Micro ATX
Hard Drive 1 –  80GB = Operating System
Hard Drive 2 – 250GB = Home (my documents)
Hard Drive 3 – 500GB = Media (videos, music & pictures)

I would like the file to end up on the desired hard drive automatically. And my main menu to display accordingly. In other words, when I click over music, under places in my computer menu, for the computer to know which hard drive to go to. The reason for wanting this setup is, to provide security for the OP, separate my private documents from my music and videos. Now I am using external hard drives. But, it just do not look right, besides the menu is funky.

Would I have to use a RAID set-up or just the partition tool. Does anyone knows of a post or tutorial on how to accomplish this? (plain English would be better).

Thank you for all the help.

---

### Post by foutes on 2011-07-13
[http://ubuntuforums.org/showthread.php?t=38062&](http://ubuntuforums.org/showthread.php?t=38062&)

This might be of some help.

---

### Post by oldfred on 2011-07-13
I keep data separate from system as I have several copies of Ubuntu. I do clean installs but keep old install and just remount my data in the new install. I prefer to have entire system on one drive including /home but my /home has just the hidden system files & folders and some of those that have data are also in my data partition(s).

I prefer a separate /data partition. Then you can easily share your data without having the conflict of the user settings in hidden files & folders. Works best if all installed systems are Debian based, see UID issues below.

The actual user settings are small. My /home is 1GB with about 3/4 of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Shared /data (NTFS)-see post #3 oldfred
[http://ubuntuforums.org/showthread.php?t=1772620](http://ubuntuforums.org/showthread.php?t=1772620)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

Opposing viewpoint on separate data partitions - post14 srs5694:
[http://ubuntuforums.org/showthread.php?t=1738065](http://ubuntuforums.org/showthread.php?t=1738065)
Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)

Another way to share:
kansasnoob's sharing and Morbius1 use of bindfs
[http://ubuntuforums.org/showthread.php?t=1495798](http://ubuntuforums.org/showthread.php?t=1495798)
HowTo: Create shared directory for local users (with bindfs).
[http://ubuntuforums.org/showthread.php?t=1460472](http://ubuntuforums.org/showthread.php?t=1460472)
With upstart script 
[http://ubuntuforums.org/showthread.php?t=1771773&page=5](http://ubuntuforums.org/showthread.php?t=1771773&page=5)

Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
Partitioning basics with some info on /data older but still relavent
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

With a larger drive you may want to review this also:
Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate them from drive to drive.

---

### Post by slotdoctor on 2011-07-14
Thank you. That did help some. somewhat confused but I will give it a go. Again thank you.

---

