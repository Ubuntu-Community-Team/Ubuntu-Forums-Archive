---
title: "Need more disk space..."
date: 2011-10-16
forum: General Help
---

### Post by Silverflyer on 2011-10-16
Hello, I am dual booting 64 bit 11.04 with Win Vista 64 bit and as it turns out, my project to play around with linux and learn the ropes is going so well, I need more disk space.  Now, there are no extra partitions.  When I installed I installed alongside windows and gave Linux 20Gbs IIRC.  How do I expand that to get more space?

---

### Post by hwttdz on 2011-10-16
1) it seems to me that any method of altering partitions where you want to keep the data is inherently a little worrying.  So the first thing I'd do is back up.  Unless you can comfortably say, "I'm fine with reformatting" you shouldn't go on.  So after having backed up any partition on which you have data to some form of media (extra hard disk, cd, dvd) which will _not_ be physically attached to the computer (accidentally reformatting the wrong hard disk is the worst) you shouldn't go on.

2) I'd burn a gparted live cd.  

3) Boot gparted, shrink a neighboring partition, grow your ubuntu partition.

4) Reboot, and you have more space. I'd run fsck on all you partitions first thing.

---

### Post by mcduck on 2011-10-16
When you say that there are no extra partitions, do you mean that instead of having installed Ubuntu into it's own partition you made a Wubi install (which puts Ubuntu into a virtual filesystem,. located inside your Windows partition)?

This guide should help in resizing the virtual disc used by Wubi:
[http://ubuntuforums.org/showthread.php?t=1625371]("http://ubuntuforums.org/showthread.php?t=1625371")
(although I really wouldn't recommend using a Wubi install in long term, it's really only suited for easy testing of Ubuntu. In long term you'll really want the extra reliability, performance and flexibility of a conventional install instead).

---

### Post by Silverflyer on 2011-10-16
> **mcduck said:**
> When you say that there are no extra partitions, do you mean that instead of having installed Ubuntu into it's own partition you made a Wubi install (which puts Ubuntu into a virtual filesystem,. located inside your Windows partition)?

This guide should help in resizing the virtual disc used by Wubi:
[http://ubuntuforums.org/showthread.php?t=1625371](http://ubuntuforums.org/showthread.php?t=1625371)
(although I really wouldn't recommend using a Wubi install in long term, it's really only suited for easy testing of Ubuntu. In long term you'll really want the extra reliability, performance and flexibility of a conventional install instead).


At first, it was just to test and get a handle on what Linux was all about.  The current HDD is one big partition, there is no separate Ubuntu partition.  It may be time to move on and Make a separate Ubuntu partition though.  Is there a way to do that and carry over my current Linux set up in a steady state without starting from scratch again?

---

### Post by mcduck on 2011-10-16
Sure, that's possible: [http://ubuntuforums.org/showthread.php?t=1519354]("http://ubuntuforums.org/showthread.php?t=1519354")

As with any tasks related to partitions, I'd recommend making sure you have a up-to-date backup of all your important files beforehands. Just in case. Of course everybody should always have such backup anyway... ;)

---

### Post by Silverflyer on 2011-10-16
> **mcduck said:**
> Sure, that's possible: [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

As with any tasks related to partitions, I'd recommend making sure you have a up-to-date backup of all your important files beforehands. Just in case. Of course everybody should always have such backup anyway... ;)


Thanks much, backups are always done and current all the time here.

---

### Post by Silverflyer on 2011-10-16
Ok, I ran into another problem.  I used EaseUS to copy the old HDD to a new one, and in preparing the new disk to follow these directions to migrate from a WUBI install to a dedicated Linux Partition I found this error.  So, now what do I do before I migrate my Linux to this partition?

---

### Post by Silverflyer on 2011-10-21
Solved, I let Win Vista do the partitioning, no mo problems and my Wubi install moved over flawlessly!

---

