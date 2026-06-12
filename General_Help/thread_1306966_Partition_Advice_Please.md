---
title: "Partition Advice Please"
date: 2009-10-30
forum: General Help
---

### Post by LenWynne on 2009-10-30
I am getting ready to do a fresh install of 9.1 and I am looking for a little advice.  My system has 2 HDs, one for the OS and the other which I use just for backing up files and storing downloaded images and music. For day to day use I seldom even mount this drive.

Since 8.1 I have been reading about having a separate home partition, and I am curious if this is really an advantage, or more work than is really necessary.  I do not want to use the second hard drive for anything other than a backup storage device. Most of the links I have found discuss creating a separate home directory after Ubuntu is already installed.

So given that I regulary back up all the important files to the storage drive would you still suggest creating a separate home directory partition on my OS drive and if so, does anyone have a link for a good guide on how to do this at the time of installation?

Thanks

---

### Post by andrewabc on 2009-10-30
I've created seperate /home partition before (still installed on hard drive), and no real difference.

I'd just install it all on one partition, that way you don't have to worry about having to resize the partitions if one of the partitions runs out of space.

I think /home is more useful if you plan on upgrading ubuntu and thus / directory would be wiped, but you would keep /home intact. If you normally do format/fresh install (recommended), then keep it on one partition. Since you have an extra 1 terabyte drive you can just copy/paste all your important files to it when you regularly install new ubuntu version.

---

### Post by louieb on 2009-10-30
A /home partition is all right. 

Having a storage partition is better.  I like what you have going now.


> still suggest creating a separate home directory partition on my OS drive and if so, does anyone have a link for a good guide on how to do this at the time of installation?


Don't know of a guide. But using Gparted -  its not hard to create partitions for the / (root) , /home and swap. Then you use the manual partition option  to tell the install to use this partition for /, /home and swap.

[GParted Documentation - general]("http://gparted.sourceforge.net/larry/generalities/gparted.htm") 

You could install VirtualBox and build a machine to practice in.

---

### Post by amjjawad on 2009-11-01
I didn't understand what exactly you want to do?

I have 2 HDDs two, one has Windows Vista and other has Ubuntu and I had some problems with partitions but looks like I managed to solve them.

Check this:[http://ubuntuforums.org/showthread.php?t=1309073](http://ubuntuforums.org/showthread.php?t=1309073)
Maybe you have similar scenario and sorry coz I didn't understand your Q!

---

