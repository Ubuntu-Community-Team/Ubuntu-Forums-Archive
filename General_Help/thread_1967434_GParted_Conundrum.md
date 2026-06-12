---
title: "GParted Conundrum"
date: 2012-04-28
forum: General Help
---

### Post by RichieB07 on 2012-04-28
I installed 12.04 alongside Windows 7 on my laptop but gave them the wrong sizes (I gave Windows the bigger partition).  Trying to fix it, I carved out a partition with GParted, but now can't seem to get it to integrate with the Ubuntu partition (See picture below).

[IMG]http://i61.photobucket.com/albums/h66/BrokenSilences07/Selection_001.png[/IMG]



I have no clue what to do now to get it integrated.  Any help would be awesome.

And yes, I know I'll have to do it in a Live CD environment, so that's out of the way with no wasted words on it :)

---

### Post by plucky on 2012-04-28
1) Delete sda7
2) Move the start of sda5 into the now unallocated space (This will take a long time depending on the amount of data it has to move).
3) Then expand sda5 into the un-allocated space which has moved to the rear of sda5.

Or 

You could re-install Ubuntu and create a /root,/home and /swap partitions.The /system partition only needs to be 15G and the rest to the /home partition.
The /Unknown if it should be /swap is very large and only needs to be the size of memory if you use Hibernate.

Good Luck

---

### Post by RichieB07 on 2012-04-28
> **plucky said:**
> 1) Delete sda7
2) Move the start of sda5 into the now unallocated space (This will take a long time depending on the amount of data it has to move).
3) Then expand sda5 into the un-allocated space which has moved to the rear of sda5.

Or 

You could re-install Ubuntu and create a /root,/home and /swap partitions.The /system partition only needs to be 15G and the rest to the /home partition.
The /Unknown if it should be /swap is very large and only needs to be the size of memory if you use Hibernate.

Good Luck

The first one did the trick, thanks!

I did also have to go into Recovery Mode and let it fix itself then reboot.  It was stuck at the login screen, but now it's all fixed.

---

