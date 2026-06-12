---
title: "How to wipe Vista and replace with XP?"
date: 2009-11-23
forum: General Help
---

### Post by OldGrantonian on 2009-11-23
I have a Vista partition and an Ubuntu Karmic partition. The Vista partition was preloaded, so Ubuntu is last on the disk.

I want to continue to expand the Ubuntu partitions and reduce the Windows partitions. As part of my efforts to reduce Windows, I want to wipe Vista and replace it with XP.

I need advice on how to do that.

The normal Google advice shows how to:

•  Install Ubuntu after Windows (which is what I did)
•  Install Windows after Ubuntu.

In both cases, the SECOND OS will be loaded at the END of the disk.

I think my case is different, because I want to install an OS at the BEGINNING of the disk. (Actually, I don't care where it goes, but I'm assuming that I would simply delete the current Windows partitions, and install XP on empty partitions.)

I would be grateful for any advice :)

---

### Post by OldGrantonian on 2009-11-24
Bump :)

---

### Post by chinmaya_n on 2009-11-24
Yes what you are assuming is exactly correct!

I suggest First install windows then Ubuntu !
1. First remove the Vista partition and install XP in resized partition
2. Then install UBuntu where ever you want on the disk
 
You can install XP in last partition  and install Ubuntu on the First... What ever is the order.... it is mind to you but not to the computer :)

---

### Post by mixmaster on 2009-11-24
If you follow the instructions for installing windows after ubuntu it should work.  The main problem is that windows install will screw up your grub loader so you will need to re-establish that afterwards.  This happens whether the new windows is at the beginning or end of the disk.

---

### Post by garvinrick4 on 2009-11-24
I believe partion 1 is boot and partion 2 and 3 can be Windows, linux will be 4 and inside of 4 will be 5 Ubuntu and 6 will be linux swap.
 Grub is always 0 and subtract 1 in the partion table. Like sda/i
will be 0/0 in grub, sda/2 will be 0/1 in grub. And so on.
One thing is for sure Windows only likes the primary partitions 1 thru 3.  If you do not have it down before you try to do any advanced partioning and grub work. Google it read about it, understand it then put it to practice. I think these are the 2 good
ones to read. I hope they are. Go over how the grub and bootloader works once you get it, it isn't so hard. 

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony?skyline=true&s=i](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony?skyline=true&s=i)

---

### Post by OldGrantonian on 2009-11-24
Thanks for all the advice and comments :)

I'll need to hibernate for a week to plan the project based on the advice.

---

