---
title: "GParted Problem"
date: 2010-07-18
forum: General Help
---

### Post by Dhanjal on 2010-07-18
I was using gparted yesterday to increase space of one of my partition in the external hard drive. I was planning to increase the size of sdb2 by 20 GB, i was moving the unallocated space above sdb3, then the power went off. Afterwards my pc stopped detecting sdb3 Songs partition, and when i ran e2fsck it gave the following error

[IMG]http://i30.tinypic.com/v5dh6g.png[/IMG]

I will run e2fsck again and post the details here

I tried using photorec to recover my songs but failed. What should i do?

I have downloaded gparted live cd but i don't think it will help me

---

### Post by techunit on 2010-07-18
Um well we need some more information... but it looks like you tryed to format your harddrive while it was mounted somehow.. You need to do this while you are in a live cd (the ubuntu cd will work) hope this helps... You should check out the Video tutorial I did on Partitioning [here]("http://ubuntuvideotutorials.wordpress.com/install-ubuntu/guide-to-partitioning/")

---

### Post by Dhanjal on 2010-07-18
The filesystem has changed from ext3 to ext2 now for some reason after e2fsck check

Also i don't why but it was sdb1/2/3 before, now it is sdc1/2/3

---

### Post by Dhanjal on 2010-07-18
> **techunit said:**
>  it looks like you tryed to format your harddrive while it was mounted somehow.. 
I had unmounted the partition before the operation yesterday, this is the file check i performed today to ask you guys the reason

---

### Post by darolu on 2010-07-18
> **Dhanjal said:**
> The filesystem has changed from ext3 to ext2 now for some reason after e2fsck check

Also i don't why but it was sdb1/2/3 before, now it is sdc1/2/3

You may want to run "fdisk -l" to see what's going on; you can also try testdisk to fix your ext3 partition.

[http://manpages.ubuntu.com/manpages/lucid/man8/fdisk.8.html](http://manpages.ubuntu.com/manpages/lucid/man8/fdisk.8.html)

[http://manpages.ubuntu.com/manpages/lucid/en/man1/testdisk.1.html](http://manpages.ubuntu.com/manpages/lucid/en/man1/testdisk.1.html)

---

### Post by iponeverything on 2010-07-18
> power went off

It was probably the worst possible time for you to lose power! Time to invest in a UPS. It would be nice if some of the available tools are able to recover data, but I would not be surprised if the inconsistent state of file system was beyond the common cases that the recovery tools can identify and fix.

---

### Post by Dhanjal on 2010-07-18
> **iponeverything said:**
> It was probably the worst possible time for you to lose power! Time to invest in a UPS. It would be nice if some of the available tools are able to recover data, but I would not be surprised if the inconsistent state of file system was beyond the common cases that the recovery tools can identify and fix.

I have got a UPS, but i had to cancel the operation in between because of the power cut. I tried testdisk in the morning but didn't succeed. Here is the error that i get when i try to open my lost partition in nautilus (I can see it but cannot access it)

[IMG]http://img841.imageshack.us/img841/8027/screenshot1.png[/IMG]

Here is the gparted_details.htm file i had saved after running e2fsck 

[IMG]http://img683.imageshack.us/img683/2564/gparteddetails.png[/IMG]

---

