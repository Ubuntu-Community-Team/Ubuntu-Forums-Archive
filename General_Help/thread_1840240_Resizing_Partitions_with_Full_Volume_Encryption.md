---
title: "Resizing Partitions with Full Volume Encryption"
date: 2011-09-07
forum: General Help
---

### Post by Frenkmeister on 2011-09-07
Hey everyone,

I got Ubuntu installed with full volume encryption (using the entire disk). Now i want to install windows(dual boot) but I'm wondering if I'll mess up my linux install if I resize the encrypted partitions.

Also, except for having windows overwrite the MBR, what other problems might I encounter?

Thanks in advance!

---

### Post by nipunshakya on 2011-09-07
First off all, welcome to the forum

^^^ If you do things correctly, you might end up with a good result.


Now that u have installed ubuntu already, i would like you to suggest few things....
Since you have used ur entire disk, windows needs some NTFS partitions with free space....so i guess u won't mind backing up ur useful datas before proceeding....and then format about 50gbs for windows 7. and then some space as NTFS partition so that you can use it in ubuntu as well as in windows to access your datas...(note this one here)
just make sure you use the gparted from LIVECD carefully and after you have installed windows, you can surely repair the MBR...

Goodluck
Regards,WinuxUser

---

### Post by Frenkmeister on 2011-09-07
Thanks for your reply and advice man.

So should I resize them while running my current ubuntu install? Or from a live disk? If I do it with a live disk, the current install with encryption would most likely get messed up right?

---

### Post by nipunshakya on 2011-09-08
^^^ I don't think it will get messed up.....Live disks are made to be tested so that you can choose if u want to use the current OS or install on your HDD.
in my opinion, using GParted from the LIVECD would be helpful for creating the unallocated space and then formatting it to NTFS partition for windows. You can make a backup, then **use gparted on a liveCD to resize your Ubuntu  partition where you want it.** Then in the new unallocated space, create a  new partition and format it for windows. gparted will flag this new  partition as primary. Boot up on your win7 installation disk and install  in the new partition.

Upto this point, i think only windows will boot up...so this is a + point as you can finish up with your remaining installations with your windows....

Then, **boot again from the ubuntu LiveCD** then run  a repair on the GRUB.


Goodluck.
Regards,WinuxUser

---

### Post by Frenkmeister on 2011-09-09
Okay, thanks again man, if I try it ill post back here how it went.

):P

---

