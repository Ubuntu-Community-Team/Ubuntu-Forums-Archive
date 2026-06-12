---
title: "Can't increase Maverick's partition"
date: 2011-10-12
forum: General Help
---

### Post by Stanoz on 2011-10-12
How do I increase the space that Maverick Meerkat occupies on my secondary storage device?
PCLOS used to be there, but I got fed up with KDE and zapped that installation. :0)
Maverick's swelling on its side of the fence. Dobby's former space is now vacant. But Gparted, I just discovered, doesn't have the muscles (that option's greyed out!) to MOVE THAT FENCE! I can't remember whether I'm using ext3 or 4. I have the fear that if I am not very careful, I'll lose data toying with my HDD. Too much important info. I'm frightened.
Please help.

-- Stanley Bob-Carl Ozoemena

---

### Post by Quackers on 2011-10-12
Is Maverick in a logical partition or a primary partition?
If you could post a screenshot of the gparted screen it may help.
Gparted has plenty of muscles, it's just a case of knowing how to flex them :-)

---

### Post by Stanoz on 2011-10-13
Quackers, Sir, thanks for that reply. My X Server's currently broken. I don't know what it was that I did wrong. I'm currently stuck with just bash. Sorry. :( No screenshots. (I'm currently posting on this site trying to find how to fix that as well.)
How, Sir, can I find out whether Maverick's on a logical or primary partition using bash?

---

### Post by Stanoz on 2011-10-13
I've just booted the system with Live CD. But I don't know how to post a screenshot to this forum, Sir. (I don't know if I'm even allowed to do that!)
I guess I'll have to do a little reading to find that out. 
In the meantime, Sir, I did this at the CLI and got this:

$sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes 
255 heads, 63 sectors/track, 38913 cylinders 
Units = cylinders of 16065 * 512 = 8225280 byte 
Sector size (logical/physical): 512 bytes /512 bytes 
I/O size (minimum/optimal): 512 bytes / 512 bytes 
Disk identifier: 0x0007b6be 
 
Device Boot       Start         End      Blocks           Id     System 
/dev/sda2         1569         38914    299975889+    5    Extended 
/dev/sda5         1569         2077     4088511         83    Linux 
/dev/sda6         2078         25035   184402418      83    Linux 
/dev/sda7        25035         38344   106906624      83   Linux 
/dev/sda8        38344       38914     4575232       82   Linux swap

---

### Post by Stanoz on 2011-10-27
[IMG]http://stanoz.com/node/3[/IMG]
[http://stanoz.com/node/3](http://stanoz.com/node/3)
Here it is, Sir. I used LiveCD to boot the machine. I then uploaded it to my website. That's the only way I could think up...

---

### Post by Quackers on 2011-10-27
Sorry, I somehow missed your replies last week!
It seems that your drive is full of partitions. Which partition is Maverick in?
To extend the Maverick partition you will need to reduce or delete the partition immediately after Maverick's then use that space to extend in to.

---

