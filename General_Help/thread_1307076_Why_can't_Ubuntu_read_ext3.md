---
title: "Why can't Ubuntu read ext3??"
date: 2009-10-30
forum: General Help
---

### Post by Paul22 on 2009-10-30
I formatted a microSD with fat32 and ext3 for my Android phone.  It's been working just perfectly for the past month or so.

Today I decided to try looking at what's in the ext3 partition, but for some reason I can not access it by any means.

I tried all four of these programs, none of which worked:
[http://tombuntu.com/index.php/2008/03/19/four-applications-for-accessing-ext3-partitions-from-windows/](http://tombuntu.com/index.php/2008/03/19/four-applications-for-accessing-ext3-partitions-from-windows/)

And I even tried using Ubuntu, which for some reason also doesn't work:

[[IMG]http://img442.imageshack.us/img442/1061/screenshot2r.png[/IMG]]("http://img519.imageshack.us/img519/7138/screenshot2d.png")

Notice Gparted correctly recognizes all the partitions, but File Browser only can recognize the fat32 portion. I tried unmounting that fat32 in Gparted, the ext3, both, etc, none worked.

Why is this? And how can I access the ext3 partition????

---

### Post by KinKiac on 2009-10-30
What happens when you open the 7.1g media in your file browser?  Does it just display the one folder for the NTFS section?  I noticed you circled the 7.1GB in nautilus but your gparted shows 7.6GiB.  As far as I know the 2 are essentially the same value.  Are you sure you cant just open the 7.1GB media and access all the partitions?
Also is it possible that your Android phone is locking up that partition for some reason?

Edit:  Also, it might be possible that your phone has created that partition with special file permissions, permissions you would not have in an Ubuntu Live session.  Ive seen a similar issue with a full install of ubuntu 9.04 that I loaded on to a thumb drive and then plugged into my desktop PC.  If I booted into my HDD and then tried accessing my thumbdrives file system, anything that required root access on the thumb drive couldnt be changed on my desktop(at least not without some messing around).

---

