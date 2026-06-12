---
title: "Partitions and hard drive space"
date: 2010-09-26
forum: General Help
---

### Post by EricLorber on 2010-09-26
I recently decided that I wanted to try out something from the Linux community because of general curiosity. I installed Ubuntu with all of the default settings and after two or three days of fiddling with this operating system I am extremely impressed. 

By default I partitioned 11 GB or so during the Ubuntu installation, which is now down to 2.8 GB because I used a usb flash drive to move my music from Windows 7 onto Ubuntu. As it is I have plenty of space for my school work and what not, but not nearly enough space to save a couple of movies on here.

How to I partition more space for Ubuntu?

---

### Post by cgroza on 2010-09-26
Use gparted and resize the ubuntu partition.

---

### Post by kyphi on 2010-09-26
Place your Ubuntu CD into the CD drive and reboot to enter a Live session.
Under the heading of System, Administration you will find the Partition Editor.
Locate your Ubuntu partition and increase the size using the left/right arrows.

If you have Windows on the same hard drive you should defragment Windows 7 before you repartition.

The following URL relating to the Partition Editor will help you:

[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by srs5694 on 2010-09-27
I recently wrote a two-part article on the topic of partition resizing for IBM developerWorks: [Part 1](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html) and [Part 2.](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-2/index.html) They may be helpful if you need more detail or run into problems.

Note that partition resizing is inherently at least a little bit risky. You should try to minimize how often you do this, especially if you're moving the start of a partition. Depending on your partition layout, instead of shrinking Windows and expanding your Linux partition into the freed space, you might consider shrinking Windows and creating a new partition in the freed space to hold data to be shared between the two OSes or to hold Linux data. That will reduce the number of partition move/resize operations, and using a separate shared-data or Linux user data partition has advantages of its own.

---

