---
title: "MFT Damaged!!"
date: 2012-06-24
forum: General Help
---

### Post by katoiam on 2012-06-24
Hello one and all,

been pulling my hair out trying to get an external (until recently Internal in old laptop) hard drive to work again.

Long story short, old laptop HDD in box, plugged into new work laptop running Winblows, running fine this morning, (in fact was running Kubuntu from it by starting from usb at start up) I was playing with settings and it crashed and had to turn it off with power button, this happened twice, then on 3rd boot, couldn't mount /home, then couldn't load grub went to grub recovery: now stuck in winblows trying out options. So far diskinternals is telling me the MFT is damaged but can recover what appears to be all of the data, but only if I pay $130, trying to get a linux live disk to help me find an open source free way of doing this, but problems of being remote and a very suspect internet connection.

Can anyone tell me if it possible to fix the MFT and the MBR? 

I have testdisk but I believe this will fix the MBR problem but I will still have a messed up partition if the MFT is buggered.

Feeling very noobish, would love any advice people can throw my way and will supply any info I can.

Much appreciated in advance,

Cheers,

---

### Post by katoiam on 2012-06-24
Just had a look at the partitions using windows disk management, all my Linux partitions come up as healthy but unknown partition, my windows partition comes up as unallocated. Having another look at it with test disk to see if I can at least get winblows to see the NTFS partition properly.

Still hoping someone can give me a bit of advice :p

---

### Post by oldfred on 2012-06-25
Testdisk does have some advanced modes.

Part of testdisk which is in the repositories or most recovery CDs. 
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)
[http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html](http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html)
[http://ubuntuforums.org/showthread.php?t=1443110](http://ubuntuforums.org/showthread.php?t=1443110)

If NTFS partition have you run chkdsk until there are no errrors?

---

