---
title: "Lazy Unmounting"
date: 2012-08-23
forum: General Help
---

### Post by libspero on 2012-08-23
Hi guys,

Converted ubuntu user now..  been running since 12.04 and loving it.

There is one thing that is causing me a bit of concern though..  attaching USB drives  (pen drives external HDDs etc).

As an Ex windows user I used to just whip them in and out and never had a problem,  however,  I notice that Ubuntu seems to be a lot more sensitive.   So far I've binned one HDD and rendered a pen drive unreadable.

I know I only have myself to blame (and it's possible that the HDD just failed of old age),  but I'm wondering if anyone else has found this and whether there is any software available for the terminally feckless to help get around the problem (I don't mind slower performance..  just don't want my drives to keep getting killed).

At the moment I'm a bit nervous about plugging anything into it  :icon_frown:

---

### Post by drmrgd on 2012-08-23
I don't have a software solution for you.  But I do want to say that it's never a good idea (Windows, Mac, Linux, etc.) to remove media without unmounting it first.  I'm betting there's not going to be any software that will allow you to remove media without unmounting it first (I could be wrong though!).  Really, unmounting only takes an extra second and will ensure that nothing gets corrupted on your device.  I'd recommend you just stick with the standard way to be safe.

---

### Post by 2F4U on 2012-08-23
I also can't recommend a seperate software solution since there already is one. If you use Unity right click on the usb icon and click "Safely remove". I always use it and never had problems with inconsistent data or corrupted drives (to be honest, I also used it this way in Windows).
There is no difference between Windows and Linux, it rather depends on the time you remove the drive, e. g. whether the data has been completely written or not.

---

### Post by ajgreeny on 2012-08-23
In 10.04 using gnome2 I make full use of the panel applet Disk-mounter which allows mounting and unmounting of internal partitions (those not in fstab) with a single click, and mounting and ejecting of USB attached disks.  I don't know if it's available for unity in 12.04, but it is certainly available in the gnome-panel classic desktop which I have for my 12.04 test partition.

It makes life so much easier when it comes to unmounting USB drives prior to removing them, and it must be worth searching for something similar for use in unity.

---

### Post by libspero on 2012-08-26
I will try to remember to always un-mount my drives in future..  looks like nobody else really has a problem with this so I guess I must have just been unlucky.

Thanks to all who replied  :)

---

