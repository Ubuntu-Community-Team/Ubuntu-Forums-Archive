---
title: "'/home' disk space ?!"
date: 2009-12-15
forum: General Help
---

### Post by chinmaya_n on 2009-12-15
I 've done a fresh install of Karmic just a day before!
I've taken backup of all my data and now i've formatted the whole system during installtion.....
I gave '/home' a separate partition (YOu can see in the attachment)

When i open gparted i could see that /home partition showing 10GB free
But when i open the home in nautilus it shows just 1.7GB free at the left bottom !!

What happend??

---

### Post by fancypiper on 2009-12-15
I seem to remember reading that some gui programs don't report disk file sizes correctly.

What does df -h report?

---

### Post by chinmaya_n on 2009-12-15
Output of **df -h**:
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              37G  5.8G   30G  17% /
udev                  2.0G  268K  2.0G   1% /dev
none                  2.0G  1.1M  2.0G   1% /dev/shm
none                  2.0G   84K  2.0G   1% /var/run
none                  2.0G     0  2.0G   0% /var/lock
none                  2.0G     0  2.0G   0% /lib/init/rw
/dev/sda5             184G  173G  1.7G 100% /home
```
If we observe 184-173=11GB!! free but it is showing 1.7Gb avail ?? WHat has happend to the remaining space ?

---

### Post by northern lights on 2009-12-15
You've stumbled upon reserved disk space for system usage.

Read [this well written HowTo]("http://newyork.ubuntuforums.org/showthread.php?p=7053432").

---

### Post by fancypiper on 2009-12-15
Also, is there anything in /home/lost+found?

---

### Post by chinmaya_n on 2009-12-15
Thanks for that help.......!!
**is there any problem if i just make it to 0% ??**
As my partition is 185GB, can i keep it to just 1% so that it reserves just 1.8GB ?!!

---

### Post by northern lights on 2009-12-15
> **chinmaya_n said:**
> As my partition is 185GB, can i keep it to just 1% so that it reserves just 1.8GB ?!!
That is a decent idea.

---

### Post by fancypiper on 2009-12-15
I would certainly try to recover space as per the link before changing reserved space.

From [HOWTO: Recover Lost Disk Space]("http://newyork.ubuntuforums.org/showthread.php?p=7053432"):

tune2fs. Reduce the space reserved for system use. By default, Ubuntu reserves 5% of linux partitions for use by the operating system. Some commands and applications do not accurately reflect reserved system space (gparted/baobab). Nautilus and the "df" command accurately display available usable space by accounting for reserved system space.

The amount of partition space reserved for this can be altered with tune2fs. Replace "X" with the percentage of disk space you wish to reserve and "XX" with the device designation.
Code:

sudo tune2fs -m X /dev/sdXX

Example: sudo tune2fs -m 4 /dev/sda1
Note: There is a reason Ubuntu reserves this space. Carefully consider if you want to change this setting before doing so.

---

### Post by chinmaya_n on 2009-12-15
> **fancypiper said:**
> Also, is there anything in /home/lost+found?

There is nothing in lost+found!!

> That is a decent idea.
Ya... I've done that, increased free space by 8GB !!:P
Thanks for Everyone:popcorn:

---

### Post by fancypiper on 2009-12-15
You emptied trash?

---

### Post by chinmaya_n on 2009-12-15
> **fancypiper said:**
> You emptied trash?

Ya.. i've done that! Just by emptying the trash bin!

---

### Post by drs305 on 2009-12-15
> **chinmaya_n said:**
> Ya.. i've done that! Just by emptying the trash bin!

There is also root-owned trash that is *not* owned by you and won't be removed simply by emptying your trash bin. The details are outlined in the Disk Space link referenced in post 4.

---

### Post by chinmaya_n on 2009-12-15
> **drs305 said:**
> There is also root-owned trash that is *not* owned by you and won't be removed simply by emptying your trash bin. The details are outlined in the Disk Space link referenced in post 4.
Yes ... i did it! 
Thanx again for everyone!

---

