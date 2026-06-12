---
title: "partition swap???"
date: 2009-12-23
forum: General Help
---

### Post by tyler_ on 2009-12-23
ok, so first off if this is in the wrong place please tell me.  although im not new to the forum world i am new to ubuntu and the ubuntu forums.

ok so after having ubuntu 9.10 for about a month i must say that i LOVE it.  but having only around 20 gigs in the ubuntu partition and the other 200 is still on the vista side has become a problem since well... i never use vista.  i found out how to mount the vista partition and be able to listen to my music and watch movies and such that are on vista while i was in ubuntu but that is such a hassle.  i was wondering if there is any way to kinda swap the partitions around.  i know i could just add space to the ubuntu side but im running out of room on both sides and have been told that expanding a partition is possible, but also a good way to fry the good ol hard drive.  

thanks any help will be appreciated.
tyler

---

### Post by pastalavista on 2009-12-23
The only way to "swap" the partitions is to back-up both completely and reformat the entire drive. You can resize the partitions without harm (usually) with the Ubuntu live CD. Boot to the "try without changes" option and open System-> Administration-> Gparted (Partition Editor). Shrink the Windows partition and expand Ubuntu. I've done it a few times with no damage.

ps. You will probably need to right-click and unmount the drives before you can make any changes. If the drives show on the desktop, I'm sure you will.

---

### Post by audiomick on 2009-12-23
Defrag the windows partition first.

---

### Post by dcstar on 2009-12-23
I would recommend shrinking the Windows partition and creating a brand new EXT3 to use as /home.

There are significant advantages to having a separate /home (do a forum search for detained info and instructions).

If you also leave some spare space you can use it to install other Linux/Ubuntu versions.

---

