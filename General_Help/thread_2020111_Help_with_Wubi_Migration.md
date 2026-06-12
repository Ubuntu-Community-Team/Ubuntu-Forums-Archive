---
title: "Help with Wubi Migration"
date: 2012-07-07
forum: General Help
---

### Post by teshnabrown on 2012-07-07
Can someone PLEASE help me resolve this error 
I am getting the message target partition can NOT be validated. I attach a image of the error

I'm following this instructions the word-for-word from this url
[http://ubuntu-with-wubi.blogspot.ca/2012/04/how-to-migrate-updated-for-release-1204.html](http://ubuntu-with-wubi.blogspot.ca/2012/04/how-to-migrate-updated-for-release-1204.html)

thz much

---

### Post by howefield on 2012-07-07
Post moved to own thread.

Please refrain from hijacking other posters threads especially when the topic has nothing to do with your problem.

Also please keep the bumps to one in 24 hours.

---

### Post by oldfred on 2012-07-07
Welcome to the forums.

As the script says, the sda2 partition has to be Linux formated, usually ext4.

Linux does not use Windows formats, but can read from NTFS or FAT. 

If you just created the sda2 partition, you need to reformat with gparted from a Ubuntu liveCD or a gparted liveCD download. If it is an older partition you were using then you have to backup your data as reformatting will erase it.

Generally the minimum number of partitions Ubuntu needs is / (root), formated ext4 (or ext3) and 10 to 25GB as a minimum in size. You also need swap but you  do not have to have swap, but should. Swap should be the same size as RAM generally and is unformated.

Basics of partitions:
[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by teshnabrown on 2012-07-08
Since wubi wasn't working I decided to just do a complete install on a  partition. Now ALL the videos I watch on youtube said I should use  Windows Disk Management and create a partition, and so i did. I created a  liveDVD and processed to install as dual boot.

installation #1
ubuntu 12.04 desktop installed successful and prompt for me to remove  liveDVD. Upon reboot I got the message "low graphics bhal bhal bhal". I  search the forum and the solution given was to reinstall ubuntu desktop. size 30GB

installation #2
unbuntu 12.04 desktop installed, reboot and load to login screen. Two  problems were... 1. I only have wireless connection and it wasn't  connecting, as such I could not do an update. 2. After shutting down  & booting into Windows. - Disk Management I realize that on the  installation #2 ubuntu DID NOT overwrite installation #1 but instead  created another partition all together. size 40GB
From Disk Management I decided to delete the 30GB, upon deleting the  partition Disk Management then turn it into a "EXTENDED PARTITION".

installation #3
Wake this morning and power on laptop I get black screen with "ERROR:  GRUB RESCUE". installation #3 fix the error and I had wireless  connection. All was good on ubuntu side, however the installation  created ANOTHER PARTITION. I need these extra partition to free up and  BACK ON MY C DRIVE NTFS. size 20GB

I want to just delete ubuntu 12.04 COMPLETELY FROM MY SYSTEM and remove  all partitions to just the C drive. Then I plan to do a FINAL  installation of ubuntu and see if it works.

I have been trying for DAYSSSSSSS now just to get a dual boot ubuntu on  the system, but ubuntu turning out to be as much of an headache as  windows, if not more. There is a shot of the partitions in both OS....THZ

---

### Post by oldfred on 2012-07-08
Whatever video said to create a partition from Windows was wrong. You use Windows tools for Windows generally and LInux tools for Linux.

You use Windows to shrink the NTFS partition to make room for Ubuntu. And reboot as Windows usually wants to run chkdsk after a resize. Always best to do that separate from the install. It sounds like you have that part done.

Then you just install Ubuntu into the unallocated space. The side by side install will shrink if possible any current systems and create new, so that is why you are getting all new partitions with each install.

Best to use liveCD and gparted. You can delete all the partition for LInux using gparted and do the auto install to the unallocated space. Or you can create partitions in gparted if you want more than the default of / (root) and swap. Often users add /home or a NTFS data partition to share data but neither is required if first starting out.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

Also best to use wired Ethernet for install. There are so many different wireless drivers that the CD cannot hold them so it usually downloads the wireless driver and updates are faster with wired and initial install usually has a fair number of updates.

---

### Post by teshnabrown on 2012-07-08
Thz ALOT Oldfred. I found this solution over Ask Ubuntu link...
[http://askubuntu.com/questions/133533/how-to-remove-ubuntu-and-put-windows-back-on](http://askubuntu.com/questions/133533/how-to-remove-ubuntu-and-put-windows-back-on)

I now have back my full C drive without partition. I will now process to install ubuntu AGAIN for the FINAL time. *fingers cross... i hope everything works,I'm SOOOO SICK off doingthe same thing over and over

---

### Post by teshnabrown on 2012-07-08
posting from firefox on my newly installed ubuntu 12.04; up and running good so far

---

### Post by oldfred on 2012-07-08
That's great! :)

---

### Post by teshnabrown on 2012-07-12
I am not seeing the option to Create a New Thread, hence I'm posting here.

Couple hours ago I was doing some work on my Windows partition; Windows has been prompting me for update from yesterday but I just postpone it like i normally do. Upon completing my task i restart and boot in ubuntu 12.04. The log in screen loads but before I could log in the screen just went black(blank). I waiting for sometime thinking there might be some processes its trying to complete; after around 10mins I was the power button to switch it off  & on agen.

Ubuntu loads to desktop and I start install LAMP then the same thing happen, the screen just went black; again i waited ...then ended up having to use the power button. System restarts. I got LAMP installed, proceeded to install myphpadmin but AGAIN the system crash with a black screen. I am clueless as to why this is happening as ubuntu was fine yesterday

---

