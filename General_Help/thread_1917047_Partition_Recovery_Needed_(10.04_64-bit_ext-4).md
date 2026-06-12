---
title: "Partition Recovery Needed (10.04 64-bit ext-4)"
date: 2012-01-29
forum: General Help
---

### Post by jkzubu on 2012-01-29
Hi all:

I need to recover a partition with critical data, or recover the data.  My main HDD is 500 GB with two main partitions (75 GB Ubuntu 10.04 ext-4; 50 GB personal data ext-4).  There is/was a 100 MB gap between these two parts.   I was intending to make a 3rd partition using gparted when I accidentally selected "Create Partition Table..."  The whole drive structure was apparently deleted and I could not restore or undo the drive structure or partitions.  

I kept working without realizing what I had done.  Later, after trying to mount my 50 GB partition did I realize the problem.  After shutdown, no more reboot and I am really bummed.

I disconnected the 500 GB drive and I am now running 10.04 from a completely different drive (250 GB).  The 500 GB remains disconnected while I research recovery options.  If I could only reset the boot sector for the 500 GB drive and restore the partitions I think I would get everything recovered and running again (with hope).  I understand the data is still written on the disk.  I can do without the OS partition, the personal data partition/files are really critical.  Your support is greatly appreciated.  Thanks.:D:D

---

### Post by Cheesemill on 2012-01-29
You could try using [Testdisk]("http://www.cgsecurity.org/wiki/TestDisk").

If it's not already installed you can install it with:
sudo apt-get install testdisk

---

### Post by winh8r on 2012-01-29
Hi,

You did the correct thing when you stopped using the drive as soon as possible after the mistaken deletion!

As a first possibility try this utility:

[http://extundelete.sourceforge.net/]("http://extundelete.sourceforge.net/")

I have not used it yet but it looks like it could be exactly what you need for your situation.

Hope this helps you.

---

### Post by jkzubu on 2012-01-29
Testdisk worked pretty well, Cheesemill.  I was able to ID the missing partitions and used Testdisk resubstiantiate the partition structure.  From the 250 GB install I was able to remount the partition and back up the files.  Fantastic!

Now part 2.  How can  I repair the original OS install to make the whole drive bootable again.  

Than you so much for the help, I successfully recovered the files and partition I needed!

---

