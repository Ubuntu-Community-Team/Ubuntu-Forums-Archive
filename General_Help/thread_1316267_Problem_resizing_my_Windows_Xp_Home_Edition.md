---
title: "Problem resizing my Windows Xp Home Edition"
date: 2009-11-05
forum: General Help
---

### Post by Helloo1234 on 2009-11-05
Hello,
 
My friend introduced me to Linux (Ubunto 9.10). I followed the tutorial on how to install it. Everything is working good the only problem is that i can not change the partition for Windows XP Home Edition. I tried to boot my PC with the CD and install from there, and i could not select the amount of Go i wanted for windows, to free up some space for Linux. Then i tried Gparted that was in the "Try Ubunto" without installing. Usually you can select resize/modify and select the amount of Go you need or want but on my PC I noticed that it says Min 320000 Go and max 320000. Therefor i can not change to lets say 200000 Go because i must stay in the range I specified.
 
The question:
 
How do i remove the min/max so that i can choose how much space windows is allowed so i can install Ubunto 9.10 and then make a shared folder?
 
Thank you for your help!!!
Helloo1234
 
P.S:
 
Systeme Information will be given on demand (If Needed)

---

### Post by wilee-nilee on 2009-11-05
Did you unmount the NTFS partition before try to re-size it, from the live cd.

---

### Post by Helloo1234 on 2009-11-05
I can not unmount it because its not even mounted.

---

### Post by wilee-nilee on 2009-11-06
So you can download a gparted is and burn it to a cd to boot from it.
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)
So let me see if I understand your situation you are trying to resize the XP with a live CD. Now if you have installed Ubuntu I think you have to turn swap off when you use the Live cd to use gparted to resize. If you haven't installed anything and you booted from the live cd you should be able to adjust the partition of XP. Have you done a wubi install and are trying to use gparted in Ubuntu to resize the partitions. 

So if you cannot resize with the live cd booted whether you have installed or not and have tried the swap off if you have installed, and it isn't allowing you then the gparted ISO may be the best option. Although I would have to wonder if the live CD is not letting you do any resizing following the standard methods that it may ne a corrupted download or burn. So if you burn a gparted or another cd make sure you do it at the slowest speed.

---

### Post by Helloo1234 on 2009-11-06
Yes i did use Gparted that was in Ubunto. Idid not install Ununto yet. i will try with a live-Cd right  now and il let ya know if it worked.

---

### Post by Commander_Keen on 2009-11-06
Do not touch the Windows Partition.
  Unless your an expert
  Unless you do not mind reformating your hard.
  Unless you have your data backedup..

Yea I know people would say not a problem.
I am personally afraid that if you mess around with the HD, it may byte you the end.

---

### Post by John Bean on 2009-11-06
Do a full disk check and defrag - possibly twice! - in Windows before attempting to resize.

---

### Post by Helloo1234 on 2009-11-06
umm.. well 1 thing you dont need to be a pro to change partitions and um 2nd i did 3 defrag and checks. i just want to know if there is an other way of changing the partitions.And if i cant get an answer here il go to my local PC store where there specialiste bound to know how to solve my probleme. only thing it probably gonna cost me so i just want to save that. 
 
Thx for any helpful replys

---

### Post by wilee-nilee on 2009-11-06
> **Helloo1234 said:**
> umm.. well 1 thing you dont need to be a pro to change partitions and um 2nd i did 3 defrag and checks. i just want to know if there is an other way of changing the partitions.And if i cant get an answer here il go to my local PC store where there specialiste bound to know how to solve my probleme. only thing it probably gonna cost me so i just want to save that. 
 
Thx for any helpful replys

No matter what you do make sure you have anything that is on the computer that you can't lose saved off the computer.

Repartitioning is quite easy, and if you just tried to a install the ubuntu and let the partitioning GUI that is part of the installation see if it will let you install side by side and use the slider at bottom to format the the partition sizes. If you try this method as long as you don't let it partition you can abort no harm done. You would use this method just to see if the install partitioner will do the work you need done. If it does then your you should be safe.

---

### Post by Helloo1234 on 2009-11-06
lol i tried all that. i dont think i made my self clear enough. I cant Partotion Windows because it says Minimum MiB is 319000 and Maximum is 320000 MiB. It wont let me resize lower than 319000MiB. I need to stay in the range specidied.

---

