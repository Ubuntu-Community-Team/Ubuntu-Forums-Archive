---
title: "Fail to use unused partitions and resize the home folder"
date: 2012-03-26
forum: General Help
---

### Post by rosingle on 2012-03-26
[SIZE=2]Hi everyone I'm a new part of Ubuntu gang. The OS has pleased me so much that today I tried to delete the Windows with the help of VirtualBox. But things turn out to be difficult when I do the cleanup... I upload the partition layout of my disk and [COLOR=Blue]hope someone can tell me how to delete the sda 5,6,8,11 partitions and also use all the unallocated space to enlarge sda 9[/COLOR]:KS. I've tried Gparted but firstly it told me to unmount the sdas whose number is higher than 5 and then when I tried to follow the instruction the sda 7 just won't unmount because it's busy, neither does the sda9 for the same reason. Then I ran to cfdisk but it failed to run because of some disk error... Here is my fdisk result. It seems that the sdas 4 and 5 have a shared area but I don't what it means. :confused:

Tks in advance! 

[PHP]Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xd85138c1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda3       744824832   765718527    10446848   83  Linux
/dev/sda4         2459648   744824831   371182592    f  W95 Ext'd (LBA)
/dev/sda5         2461696    79554559    38546432   83  Linux
/dev/sda6        79556608   188170239    54306816   83  Linux
/dev/sda7       221378560   221779967      200704   83  Linux
/dev/sda8       221782016   358520831    68369408   83  Linux
/dev/sda9       358522880   401106943    21292032   83  Linux
/dev/sda10      722522112   744824831    11151360   83  Linux
/dev/sda11      401108992   722520063   160705536   83  Linux
/dev/sda12      188172288   221376511    16602112   82  Linux swap / Solaris

Partition table entries are not in disk order[/PHP][/SIZE]

---

### Post by Vaphell on 2012-03-26
boot system from livecd/liveusb and run gparted, hdd won't be in active use and you will get to make changes.

no wonder sda5 and sda4 are in the same area, sda4 is a primary partition (sda1-4) and it is extended which means that it hosts logical partitions inside (sda5+). That bright blue frame is sda4 and it has tons of boxes inside, yes?

---

### Post by rosingle on 2012-03-26
What a clear explanation! Tks! I'll try the live cd tomorrow and see if there are some other problems. Tks!

---

### Post by Vaphell on 2012-03-27
most likely you will have to update /etc/fstab file (most likely partition identifiers will change and you will have to inform the system about their new identity)
also back valuable things up - something goes wrong and you get serious data loss on your hands.

---

