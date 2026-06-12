---
title: "External HDD + Karmic = GDU using CPU"
date: 2009-11-02
forum: General Help
---

### Post by frankstrudel on 2009-11-02
Hi

I recently upgraded to karmic from jaunty, muchly satisfied for the most part; thanks for all the great work that has gone into it!

Only problem I haven't been able to solve so far is a massive use of CPU when my external hard drive  is plugged in and turned on (whether from bootup or afterwards).

Fluctuating between 65-100% of each core is used, mainly by gvfs-gdu-volume monitor, closely followed by gdu-notification-daemon and update-notifier. All three only take up so much CPU between when it is plugged in and 'safely removed'. 

GDU is, I gather, gnome disk utility, which while I have no idea what it does, would seem to make sense that it has problems coincident with the external hard drive. The update-notifier CPU usage has me bewildered, however - unless it is trying to suggest that I update something?

I have tried a solution which has apparently worked for a similar problem **[here,]("http://ubuntuforums.org/showthread.php?t=1307926")** but to no avail.

Any other ideas?

Thanks,
Frank

---

### Post by jlindbergh on 2009-11-04
I also noticed this as I just answered in this thread [http://ohioloco.ubuntuforums.org/showthread.php?p=8243464](http://ohioloco.ubuntuforums.org/showthread.php?p=8243464)

When reading the post you linked to ([http://ubuntuforums.org/showthread.php?t=1307926](http://ubuntuforums.org/showthread.php?t=1307926)) I realized that I manually mounted some disks using mount -a. I did that because I'd added some disks in fstab without creating the directories to which they mount... I'm hoping this will be ok on my next reboot.

---

### Post by jlindbergh on 2009-11-04
It's not okay after rebooting. Help!

[update]: Got a workaround from the other thread ([http://ubuntuforums.org/showthread.php?p=8243537](http://ubuntuforums.org/showthread.php?p=8243537))

---

### Post by frankstrudel on 2009-11-04
I have no ntfs partitions either on my internal or external hdd, and as not mounting these is a suggested workaround [in the other thread]("http://ubuntuforums.org/showthread.php?p=8243537"), I think I must have a different problem..?

---

