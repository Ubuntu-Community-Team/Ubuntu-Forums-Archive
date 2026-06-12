---
title: "How can I shrink my Windows parition?"
date: 2012-05-20
forum: General Help
---

### Post by asad.bukhari on 2012-05-20
I've undertaken a project to set up my netbook so that it dual boots with Windows 7 and Kubuntu, so I'm new to linux.

I installed Kubuntu through Wubi Installer allocating 17 GB to it. The rest of my 150 GB hard drive consists of Windows 7, which was the original OS.

I'm now stuck trying to figure out how to create a third "storage" partition for my personal data (documents/music/pictures/etc), and mount it so that I can access it from Windows and Kubuntu.

Although Windows takes up about 50 GB on its 132 GB partition, the Windows partitioning tool does not let me shrink the hard drive... So I can't open up the remaining space for a storage partition. I already went through all the processes (disk defragmentation, chkdsk, etc) to try to consolidate data and get the partition tool to shrink, but had no luck.

I wanted to use GParted to shrink the partition but my netbook doesn't have a CD drive and I don't have an external. When I use GParted in Kubuntu, the Windows partition has a lock next to it meaning that I can't shrink/resize it, which I think is normal.

**How can I shrink the Windows partition to open up space in order to create a Storage partition?**

OR

Is there a simpler way to access my personal data in the Windows partition from Kubuntu?

---

### Post by miegiel on 2012-05-20
You can't resize partitions in use. So you will need to boot to an OS that is not on your hard disk. With a netbook (without CD player) booting from an USB stick is the easiest option. If you [create an ubuntu live USB installation disk]("https://help.ubuntu.com/community/Installation/FromUSBStick#From_Ubuntu_Linux") and tell it to "try ubuntu". Once it's booted to the desktop, you can use gparted from the USB disk. One thing to keep in mind is that the "live CD" automatically uses the swap partition on your netbook's disk. IIRC you can right-click on the swap partition in gparted to tell ubuntu to stop using the it.

---

### Post by wiggly81 on 2012-05-20
gparted has a standalone boolable iso that i often use to edit partitions 
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by wangmf8877 on 2012-05-20
You can use shrink function in Win7 to resize your C:\ disk. The reason you can't do it, is because your system protection is "ON".

You need to turn off system protection of C:\ disk, and shrink it to proper size you want, then turn on the system protection again.

Good luck!

---

### Post by wilee-nilee on 2012-05-20
I would backup that W7 before doing anything, honestly if the W7 partitioner, which does run live wont do it, gparted may brick your setup, there are unmovable files in windows if moved can really cause problems.

Get a partitioner that will move all the W7 files to the front of the disc and use the W7 partitioner. Defragg before moving and after before the partition size change.

As well the wubi is not designed for long term use read here what the designer has said.
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)

If you decide a partitioned dual boot suits you that wubi can be moved to a partition, there is a thread on the forums just for that.

---

