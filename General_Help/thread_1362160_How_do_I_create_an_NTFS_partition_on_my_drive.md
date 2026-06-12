---
title: "How do I create an NTFS partition on my drive?"
date: 2009-12-22
forum: General Help
---

### Post by scott_s_06 on 2009-12-22
I dual boot 7 and Ubuntu, 7 is on my first hard drive and Ubuntu is on the second hard drive, the Ubuntu drive is 1.5Tb and I would like to partition about 1Tb of it to use on windows.  How can I do this? It is a fresh install of Ubuntu 9.10

Thanks for the help as always!

---

### Post by Ocxic on 2009-12-22
you could use windows to Format the partition, it does not matter how it is formated before you do this so long as the partition exists. in Ubuntu GParted can do this, but you need to install ntfs tools from synaptic to actually be able to format as NTFS, i forget what it is called tho.

IF the partition is already there I would just use windows to format it. just be careful.

---

### Post by x33a on 2009-12-22
@ Ocxic,

The package is called ntfsprogs.

[http://packages.ubuntu.com/search?keywords=ntfsprogs](http://packages.ubuntu.com/search?keywords=ntfsprogs)

---

### Post by oldfred on 2009-12-23
Three years ago I was just starting to convert to Ubuntu and created a share FAT32 partition for data that I might want in both including firefox and thunderbird profiles and photos. Now I have converted that to NTFS and have a new /data partition just for ubuntu data that I know I will not want in windows. Now I am in Ubuntu most of the time.

You may want to have more than one partition for data with a drive of that size, just to make it easier to backup.

---

### Post by scott_s_06 on 2009-12-26
I tied doing it in windows, but the only option it gave me was to delete the entire partition.  I installed ntfsprogs and GParted, and the partition that is highlighted is the one that Ubuntu is installed on and that I would like to make smaller, so that I can add an NTFS partition to that drive, but when I click on partition all the options are not available.  What am I doing wrong?

---

### Post by oldfred on 2009-12-26
The keys are the lock symbol. You cannot modify partitions that are mounted or you can only use gparted to view while in your Ubunut system unless you can unmount other drives.

You need to use the liveCD to edit partitions. Even the liveCD may use the swap partition so you may have to click on it and swapoff.

---

### Post by oldtraveler on 2009-12-26
The free Macrium Reflect can be downloaded and installed in Windows.  Run it from Windows and you can re-size any partition you wish on either disk.

---

### Post by Sef on 2009-12-26
I like to partition with the [GParted]("http://gparted.sourceforge.net") disc.

---

### Post by x33a on 2009-12-26
your partition structure is as such pretty weird.

no need to allocate 12 gb for swap, and not necessary to keep it in an extended partition.

my advice would be to delete the swap partition. then merge that space with the other space.

then

1. leave 1 TB for windows.
2. create a swap of 2-4 GB (depending upon your ram).

note: do all this using a live cd, preferrably gparted live, as sef already said.

---

