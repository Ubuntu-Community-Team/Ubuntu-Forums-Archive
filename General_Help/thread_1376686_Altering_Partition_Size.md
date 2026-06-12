---
title: "Altering Partition Size"
date: 2010-01-09
forum: General Help
---

### Post by rsteph49 on 2010-01-09
Is there a way to alter an existing Partition size (partition size and/or drive letter) Pre installation of Unbuntu?
 
I've got a computer with WindowsXP on one partition, and I'm looking to possibly install Ubuntu on the other so I can boot to it sometimes, and start learning how it operates. However, I wanted to increase the size of the partition that Windows has first, to make the two partitions more equal. I've got free space on my drive (unused space) to increase the existing partition - I was told that this could be done with the Ubuntu installer disk.
 
Can anyone help me out with how to do this (if it's in fact possible)? Or do I need to go get a copy of Partition Magic, or other similar program to handle this prior to installation?
 
Any help would be greatly appreciated, thank you.

---

### Post by mk1w86 on 2010-01-09
You can use GParted on the Ubuntu live CD. :D

Goto System>>Administration>>GParted

You can also do the same during Ubuntu installation by selecting partition manually at the partitioning stage of the installation.

Before resizing any partition make sure you back up any important data and defragment the Windows partition first.

---

### Post by rsteph49 on 2010-01-09
I tried this, for some reason, even though I can expand the secondary partition (currently sitting at just under 500GB; I still can't seem to adjust the Primary Drive (where Windows resides) past the approx. 137 GB it's currently at - I'm wanting to use the rest of my 1TB drive and make both drives roughtly 500GB.
 
This is a brand new drive, the only copy of XP I could find around was a very old copy (Pre Service Pack 1) which is why the partition was not initially set up to the size I wanted, however I've totally patched the OS to Service Pack 3 etc.
 
Is there any trick to using GParted to increase a partition past it's original size? Does the fact that the partition is a boot partition change anything?

---

### Post by mk1w86 on 2010-01-09
Although this does not solve your problem are you sure you want XP on such a large partition for defragmenting etc..  Maybe create a separate NTFS formatted partition for your data.

You could also create an new XP install disk with SP3 by slipstreaming it using a tool such as nlite:

[http://www.nliteos.com/](http://www.nliteos.com/)

---

### Post by Jackzor on 2010-01-09
Something you COULD do is just make a partition to use for both operating systems like I have done. I have windows 7 (50Gb ntfs) and Ubuntu (50Gb ext4) And another "passthrough" partition(150Gb ntfs) for use over both OS's.I think that is a much better way to go.

---

### Post by noob555 on 2010-01-09
Not really a direct response, but perhaps the smart thing is to create a shared partition that both Windows and Linux and read and write to.  Most people seem to recommend FAT32, but I'd look around and do some independent research as there's a bunch out there.

---

