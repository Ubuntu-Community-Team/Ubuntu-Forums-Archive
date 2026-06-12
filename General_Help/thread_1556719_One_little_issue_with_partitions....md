---
title: "One little issue with partitions..."
date: 2010-08-19
forum: General Help
---

### Post by carpediem_dt on 2010-08-19
Greetings.

I installed Ubuntu 10.04 Lucid Lynx on my laptop. I chose to make  partitions manually. I like to keep my music and other stuff on  different partitions. Well, I made three on my 500 GB hard disk:
A= 150 GB (on this partition I installed Ubuntu)
B= 200 GB 
C= 150 GB

I thought I'd see the partitions B and C on "places" and mount them easily. Simply as that. But they just didn't showed up.

Then I used gparted to try to work it out. I formated B and C to FAT32. Now, on "places", I can only see B, but not C.

The thing is, I want to be able to mount both partitons, B and C, directly from "places". 

Would you help me, please?

Thank you in advance and I wish you ¡días largos suficientemente buenos!

---

### Post by oldfred on 2010-08-19
If you are going to have all your data in different partitions you do not need a large system partition. I use 20-25GB for root and with lots of programs have used about 6GB. My /home uses about 1GB and everything else is either in shared NTFS partition or /data. I now use windows so little i do not have much in shared.

You can directly mount your partitions into /home or mount them somewhere else (so they do not show twice in places) and link them into /home. I replaced the standard folders in /home with links to my other partitions. 

I also recommend NTFS over FAT. If you have any files over 4GB you will not be able to save them in FAT.  I only use FAT for small partitions (<4GB) or devices like my camera flash card that has to have FAT.

Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Share Windows partition:
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)
Link XP my docs
[http://www.techsupportalert.com/how_to_move_my_documents.htm](http://www.techsupportalert.com/how_to_move_my_documents.htm)

How to Multi-boot (Maintain more then 2 OS) old grub
[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)
Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions of data linking from above blog, based on more from comments
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

---

### Post by carpediem_dt on 2010-08-19
Hmm... I haven't thought about that. You are right, I don't need much space for root.

But, I don't have Windows. I only have Ubuntu. I only want to be able to mount both partitions by simply clicking on them on "places". Only for security.

Why? Cause one time I installed Ubuntu with no partitions then one day it crashed and I lost all my important data. Now I want to keep my stuff on other partition to be able to do whatever I want on Ubuntu, and if I mess it up, I want to keep my stuff intact. 

Why two extra partitions? One to keep my stuff like music, media, etc and the other one to... I don't know, the same reason... maybe one day I need to install Windows on it. Haha.

So... how do I do it? =)

---

