---
title: "Re-size Ubuntu Partition"
date: 2011-03-23
forum: General Help
---

### Post by lightmas on 2011-03-23
Hi all 

I am not sure where to post this so move please if its the wrong place. A few weeks ago i decided to try out Ubuntu, so I installed it as a dual boot, along with Windows 7. Now i have decided to switch fully to Ubuntu, so I have formatted the windows partition. Now however i am not sure how to allocated the unallocated space and expand the Ubuntu partition. Is even possible? 

Cheers

Rhys

p.s [http://tinyurl.com/683c3df](http://tinyurl.com/683c3df) << a screenshot (I am using a live CD of Ubuntu to use gparted.

---

### Post by drs305 on 2011-03-23
I wrote this guide to help expand / which offers some advice.
[http://ubuntuforums.org/showthread.php?t=1219270]("http://ubuntuforums.org/showthread.php?t=1219270")

Looking at your specific situation, you will need to expand the extended partition (sda4) and then expand sda5. Do this using Gparted from the LiveCD. 

Two things to remember, even from the LiveCD, you will need to unmount the swap partition. Also don't forget to back up irreplaceable data - Gparted is great but accidents do happen...

---

### Post by oldfred on 2011-03-23
drs305 link to his instructions is very good. 

But I would like to emphasize my preferred choice(s) of smaller system partitions and separate /home or /data partitions. He mentions a separate /home in his link.  

Your system partition currently is not large and you have to have /home inside it now. But /home has two uses - one for your user settings and the other is all your data. Your user settings are small, but of course you data can be any size depending on what you save.

Having a separate /home makes it easy to reinstall the system in case you have to or if you use a clean install for a new version. And just creating a /data partition lets you store data in the current used space if you desire. 

Preferred choices depend a lot on what you plan to do, and even that choice changes over time, so there is no wrong choice.

---

### Post by lightmas on 2011-03-25
Thanks, the first suggestion worked fine :)

All this Ubuntu stuff is new to me :)

---

### Post by drs305 on 2011-03-25
> **lightmas said:**
> All this Ubuntu stuff is new to me :)

It was new to most of us not too long ago.

If you didn't make a separate /home partition, and desire to do so once you become more familiar and comfortable with Ubuntu, it's not difficult. There are threads on this forum or links - just search for "separate /home" or "separate home".

If you don't have any other questions regarding the current thread, you can mark it SOLVED via the 'Thread Tools' link at the top right of the first post.

Happy Ubuntu-ing !

---

