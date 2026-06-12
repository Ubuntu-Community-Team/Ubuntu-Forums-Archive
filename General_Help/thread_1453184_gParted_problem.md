---
title: "gParted problem"
date: 2010-04-12
forum: General Help
---

### Post by pupEOkami on 2010-04-12
:confused:
greetings fellow ubu-guru's

not sure if this post belongs here (please redirect if need be)

  I seem to be running into a small issue about how my 1TB SATA hard drive has been formated. In gParted. just an average format like you would do any hard drive (with out) partitions.i then make sure drive is unmounted of course. upon completion of the drive format i notice that 14.81GB of space is still being used or takenup by something i for the life of me cannot figure out. if anyone has some better ways to format in ext4 please give me your ideas.

*pay no attention to /dev/sdc1 it has always been a primary means of storage and is sane*

#Also upon formating the hard drive is locked out to where everything #is read only 
#so i do the chown -R puppy : puppy /mnt/archivetwo

##screenshots attached along with my outputs if this helps.##

root@pupsden:/home/puppy# fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x014681b2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d3a61

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   83  Linux

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfa68fa68

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1      121600   976751968+  83  Linux

Disk /dev/sdd: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x78666a9d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       12161    97683201    7  HPFS/NTFS

root@pupsden:/home/puppy# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              71G  9.0G   58G  14% /
udev                  1.7G  316K  1.7G   1% /dev
none                  1.7G  580K  1.7G   1% /dev/shm
none                  1.7G  380K  1.7G   1% /var/run
none                  1.7G     0  1.7G   0% /var/lock
none                  1.7G     0  1.7G   0% /lib/init/rw
/dev/sdc1             917G  276G  595G  32% /mnt/archive
/dev/sdb1             917G  200M  871G   1% /mnt/archivetwo
/dev/sdd1              94G   92G  2.0G  98% /media/Maxtor100G



thank you ubuntu team . you guys have always been there for me when i have come close to giving up:KS:KS:KS:KS

---

### Post by oldfred on 2010-04-12
First a 1TB drive is not 1TiB.
MB vs MiB
[http://en.wikipedia.org/wiki/Binary_prefix](http://en.wikipedia.org/wiki/Binary_prefix)
[http://www.osforge.com/news/001337.html](http://www.osforge.com/news/001337.html)

Then when you format it, the ext4 is journalized so it reserves space for the journal. This improves performance and allows error correction for the cost of a small amount of space.

---

### Post by pupEOkami on 2010-04-13
> **oldfred said:**
> First a 1TB drive is not 1TiB.
MB vs MiB
[http://en.wikipedia.org/wiki/Binary_prefix](http://en.wikipedia.org/wiki/Binary_prefix)
[http://www.osforge.com/news/001337.html](http://www.osforge.com/news/001337.html)

Then when you format it, the ext4 is journalized so it reserves space for the journal. This improves performance and allows error correction for the cost of a small amount of space.

so ext4 needs to take up 14Gb of my hard drive for journaling ???

thats bogus :(

i want to hear more from other users about this . then if it has to be this way . i will mark it solved

---

### Post by akakingess on 2010-04-13
> **pupEOkami said:**
> so ext4 needs to take up 14Gb of my hard drive for journaling ???

thats bogus :(

i want to hear more from other users about this . then if it has to be this way . i will mark it solved

Small price to pay for the extra effort/use of saving data in my opinion ;)

---

### Post by oldfred on 2010-04-13
I forgot that it also reserves some space to make sure you do not crash the operating system. If you do not have an operating system you can tune out some of the space.

[http://blog.flexion.org/index.php/2010/01/07/recovering-reserved-space-ext4/](http://blog.flexion.org/index.php/2010/01/07/recovering-reserved-space-ext4/)

---

### Post by pupEOkami on 2010-04-13
> **oldfred said:**
> I forgot that it also reserves some space to make sure you do not crash the operating system. If you do not have an operating system you can tune out some of the space.

[http://blog.flexion.org/index.php/2010/01/07/recovering-reserved-space-ext4/](http://blog.flexion.org/index.php/2010/01/07/recovering-reserved-space-ext4/)

okay well its official then , i wont mess with it anymore and consider this [solved] . 

thankyou guys for your support :D

---

### Post by pupEOkami on 2010-04-13
:lol:

---

