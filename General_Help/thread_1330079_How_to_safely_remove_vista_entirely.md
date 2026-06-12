---
title: "How to safely remove vista entirely?"
date: 2009-11-18
forum: General Help
---

### Post by ucal on 2009-11-18
All right, linux has it's quirks, and Ubuntu has more of them, but I'd still like to safely remove vista entirely from this laptop, to make room for an Arch Linux boot.  I assume I can do this by just deleting the partitions that vista is on.  The problem is that 

1)I'm not sure it's safe to delete a specific partition. It contains a file called  ACERBOOT.ISO  

2)I'm not sure that deleting the partitions would reflect in the GRUB.  How do I edit that?

Right now, I think I would be satisfied if I were to just delete the partition that most of the vista data is on (I can back it up easily), keeping that questionable partition, and then editing GRUB so vista doesn't show up.

---

### Post by anthony62490 on 2009-11-18
Correct me if I am on the wrong track here, but one way to completely remove Vista is to run a live CD program called [KillDisk]("http://www.killdisk.com/"). It goes through your hard drive and sets each individual bit to "0". Takes a long time, but Vista will be COMPLETELY removed (along with anything else you had on the drive).

Is this what you're looking for?

---

### Post by ucal on 2009-11-18
> **anthony62490 said:**
> Correct me if I am on the wrong track here, but one way to completely remove Vista is to run a live CD program called [KillDisk]("http://www.killdisk.com/"). It goes through your hard drive and sets each individual bit to "0". Takes a long time, but Vista will be COMPLETELY removed (along with anything else you had on the drive).

Is this what you're looking for?

Well, as long as it can be limited to certain partitions, it would probably work for me, but it seems like overkill.  What I really want to know is if it's safe to remove (using killdisk, or other more conventional methods) a specific partition along with the partition that most of the vista data is on, and how to remove vista from GRUB.

EDIT: While I'm at it, are there any inherent risks to dual booting particularly to the hard drive?

---

### Post by Herman on 2009-11-18
> Well, as long as it can be limited to certain partitions, it would probably work for me, but it seems like overkill. What I really want to know is if it's safe to remove (using killdisk, or other more conventional methods) a specific partition along with the partition that most of the vista data is on, > 1)I'm not sure it's safe to delete a specific partition. It contains a file called  ACERBOOT.ISO  I would be reluctant to delete something like that if you think you might want to use Vista in that computer again someday. The best people to ask about that would be ACER tech support.
One idea you might consider would be to make a backup of your partitions with something like clonezilla or partimage first, or even a dd command. If you do that you should be able to safely delete the partition and restore it again some day if you ever decide you want to.
> and how to remove vista from GRUB.If you're using Karmic Koala, after Windows has been safely deleted, just run 'sudo grub-mkconfig -o /boot/grub/grub.cfg', and your GRUB Menu will be fixed.
```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```
> EDIT: While I'm at it, are there any inherent risks to dual booting particularly to the hard drive?     None at all.

---

### Post by Bjalf on 2009-11-18
> **ucal said:**
> 1)I'm not sure it's safe to delete a specific partition. It contains a file called  ACERBOOT.ISO
My guess is that you have an Acer laptop (well, not necessarily a laptop), and this is the recovery partition that contains an image of the recovery CD. I'd just burn the sucker to a CD and stuff it in a drawer somewhere.

> I haven't tried that but i was able to get to cmd prompt with a windows 7 dvd. so i ran chkdsk. was able to get my computer running again. unhid the **recovery partition** burnt the **acerboot.iso**. restarted booted from cd. it went into the erecovery module and is currently installing vista. fingers crossed it will work.[http://forum.notebookreview.com/showthread.php?t=378852&page=2](http://forum.notebookreview.com/showthread.php?t=378852&page=2)

---

### Post by ucal on 2009-11-18
> **Bjalf said:**
> My guess is that you have an Acer laptop (well, not necessarily a laptop), and this is the recovery partition that contains an image of the recovery CD. I'd just burn the sucker to a CD and stuff it in a drawer somewhere.

[http://forum.notebookreview.com/showthread.php?t=378852&page=2](http://forum.notebookreview.com/showthread.php?t=378852&page=2)

Okay, sounds good.  I wonder what all the other stuff in that partition is.  I think I'm going to keep that partition (it's only 14 gigs).  And I found out how to edit the boot menu from another post.  So fingers crossed, hopefully vista will be removed from my system by the end of the day (have to get access to my external hard drive so I can back up everything important).

---

