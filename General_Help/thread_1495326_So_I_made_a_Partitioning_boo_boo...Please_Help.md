---
title: "So I made a Partitioning boo boo...Please Help"
date: 2010-05-28
forum: General Help
---

### Post by Hostie on 2010-05-28
Ok, so yes i know this was stupid.... but here goes...

well, i have (sorta) lucid installed on my laptop.  going home this weekend and wanted to partition off 10gigs for xp.  never partitioned inside of linux before but i like to learn. 

so i was messing with it and went to disk manager and told it to create unpartitioned space, and i kinda wasnt thinking and kinda did it to the entire drive and rebooted and quickly realized i screwed up bad.  havent touched it since.  any hope as for undoing that so that i have the drive back?

---

### Post by pytheas22 on 2010-05-28
You should boot to an Ubuntu live CD (don't boot to any operating systems installed on the damaged disk or you run the risk of making things worse) and then install the tools testdisk and gpart.  You can install them using the Software Center or by typing:
```

sudo apt-get install testdisk gpart
```

To run the tools, type "sudo testdisk" or "sudo gpart" in a terminal.  I would start with testdisk and use its option to "Analyse current partition structure and search for lost partitions."  It can usually find previously deleted partitions and restore them.

gpart (note that it's different than gparted, which is also a partitioning tool) can also be used to recover lost partitions, if testdisk fails.  I don't have time right now to give instructions on how to use it, but you should be able to find them on the Internet.

In a worst case, if neither tool is able to restore the previous partition table, another of testdisk's options is to search for and recover individual files even if the disk's partitions or file systems are messed up.  So you can at least recover important data.

---

### Post by Hostie on 2010-05-28
Crossing fingers and booting into a live cd....ill post results

---

### Post by Hostie on 2010-05-28
by the 9 divines its fixed!

Thanks pytheas, that was clutch!

---

### Post by pytheas22 on 2010-05-28
Good to hear :)

---

### Post by dino99 on 2010-05-28
mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

