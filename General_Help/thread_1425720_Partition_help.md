---
title: "Partition help"
date: 2010-03-09
forum: General Help
---

### Post by agkq62 on 2010-03-09
I have just used Clonezilla to copy from a 60gb HD to a 40gb HD. Everything works fine but I now have two partitions (see screenshot) The sda3 was originally unallocated so I used Gparted on the LiveCD to try and expand the sda1 partition but couldn't do that. Then I formated the sda3 to ext4 and thought I could then add it to sda1 but as usual my thoughts were wrong. Basically I haven't a clue what I am doing with Gparted. Could some kind person explain simply how to get back to one partition.

Many thanks.

---

### Post by L0neRanger on 2010-03-09
Looks like you have to install from scratch.

There is a swap partition in between your sda1 and sda3. This might be the result of your clonezilla operation.

It would not be possible to merge sda1 and sda3 unles they are contiguous spaces on the hard drive.

Alternatively, you could:
* Remove the swap partition for now.
* Delete sda5, sda2 and sda3 - in that order
* Make a swap partition at the end of your hard drive.
* Extend your current drive: sda1

---

### Post by audiomick on 2010-03-09
Firstly, there is no Data in sda3, is there? As I understand you, there shouldn't be, and the "used" that is shown is probably just the file system overhead. The reason for asking is that the following suggestion will destroy any data that is in there.

Theoretically, you need to:
Delete the partition sda3.
Expand the extended partition to the end of the drive.
Move the swap partition to the end of the extended partition. To do this, you have to expand it to fill the space, then shrink it down to the size you want.
Shrink the extended partition down to the size of the swap partition.
Expand sda1 into the free space that is now adjacent to it.

This will probably take you a while.
You should backup anything important on the computer before you start, just in case.
You should do this using gparted from the live CD, and even then you will have to unmount the swap partition before you can start work. A right click on the swap partition should offer you the option to unmount, I think.

There is some reading about partitioning here
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by agkq62 on 2010-03-09
Thanks for the quick replies, there isn't any data in either partition so I'll blunder into solution two.

Has Clonezilla done this because the HDs were different sizes?

---

### Post by agkq62 on 2010-03-09
Hey guys, I've done it. Many thanks.

---

