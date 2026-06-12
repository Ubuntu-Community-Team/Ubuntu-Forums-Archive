---
title: "Can I triple boot Xp/Ubuntu 9.04/Ubuntu9.10"
date: 2009-12-02
forum: General Help
---

### Post by HandLotion on 2009-12-02
My current setup is a dual-boot with Xp/Ubuntu 9.04. I'd like to add the Ubuntu 9.10 as a third boot option.  Can I do that from one hard drive?  I have 26.4 GB free in the Ubuntu 9.04 partition, so I'd like to use the bulk of that for Ubuntu 9.10.  

My current hard drive setup is:


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           4       32098+  de  Dell Utility
/dev/sda2   *           5        4848    38909430    7  HPFS/NTFS
/dev/sda3            4849        9210    35037765   83  Linux
/dev/sda4            9211        9732     4192965    5  Extended
/dev/sda5            9211        9471     2096451   82  Linux swap / Solaris
/dev/sda6            9472        9732     2096451    b  W95 FAT32

---

### Post by hardfire_avk on 2009-12-02
Ok! when you already have ubuntu 9.04 installed then why do you need ubuntu 9.10 , it makes no sense acutally. and it seems to do that u may need to create a new partition.

---

### Post by HandLotion on 2009-12-02
I tried Ubuntu 9.10 once and had to regress to Ubuntu 9.04.  I want to try Ubuntu 9.10 again with a fallback position of having Ubuntu 9.04 available.  My question is will I have an issue when I create a new partition for Ubuntu 9.10 under gparted?  Can I safely resize the 9.04 partition downwards? ? Do I need a separate swap partition as well?  Am I going to have trouble?

As XP and Ubuntu 9.04 run from primary partitions, can I even run 9.10 as a third boot option from an extended partition?

---

