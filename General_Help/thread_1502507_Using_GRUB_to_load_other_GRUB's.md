---
title: "Using GRUB to load other GRUB's"
date: 2010-06-05
forum: General Help
---

### Post by Graham1 on 2010-06-05
Hi

Currently, I'm using XOSL to load other Linux distro's (Ubuntu, Fedora and openSUSE, each with GRUB installed into their own partition). Just wondering, if it is possible to install GRUB to the MBR which can then load each distro's GRUB?

:)

---

### Post by sdennie on 2010-06-05
Yes.  What you are describing is called chainloading.  It's very easy to do and a google search for "grub chainloading" will push you in the right direction.

---

### Post by Graham1 on 2010-06-05
> **sdennie said:**
> Yes.  What you are describing is called chainloading.  It's very easy to do and a google search for "grub chainloading" will push you in the right direction.

Hi sdennie

Thanks for your reply :). I've had a quick look but I'm unsure whether I can install GRUB directly to the MBR or install to a partition. If partition, I could use the partition (FAT32) that XOSL used (or should I use ext?). I would like to keep each distro's GRUB intact and would prefer to install directly to MBR but would this automatically detect by exisiting partitons or would I need to add these manually.

:)

---

### Post by sdennie on 2010-06-05
I'm not familiar with XOSL but, from any of your linux distros, (or a live CD), you should be able install grub to the MBR with a configuration file full of chainloads to other instances of grub living at the partition level.  How you choose to do that is up to you.  In the past, I've added all the chainloads to my "main" OS and had all the other OS's install grub at the partition level.  The partition level grubs don't need to be aware of each other.  As long as the MBR instance of grub can chainload to each partition, all will be well.

---

### Post by oldfred on 2010-06-05
I am using old grub to boot some of the older systems and I have a grub2 partition on a USB to loopback boot ISOs.

Herman has info on both grub & grub2 partitions
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition)
Chainbooting grub2, install to partition & Make CD or floppy - saikee
[http://www.justlinux.com/forum/showthread.php?threadid=152790](http://www.justlinux.com/forum/showthread.php?threadid=152790)
Herman on separate grub partition:
[http://ubuntuforums.org/showthread.php?t=1320270](http://ubuntuforums.org/showthread.php?t=1320270)
Grub partition slakkie
[http://blog.opperschaap.net/2009/11/13/all-your-grub-are-belong-to-us/](http://blog.opperschaap.net/2009/11/13/all-your-grub-are-belong-to-us/)
grub2 partition
[http://rxezlqu.wordpress.com/2010/04/07/separate-boot-partition-vs-dedicated-boot-partition/](http://rxezlqu.wordpress.com/2010/04/07/separate-boot-partition-vs-dedicated-boot-partition/)

Grub2 partition discussion:
[http://ubuntuforums.org/showthread.php?t=1465772](http://ubuntuforums.org/showthread.php?t=1465772)

---

