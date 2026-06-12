---
title: "Checking disk integrity on boot doesn't seem to work"
date: 2010-07-30
forum: General Help
---

### Post by RobertL on 2010-07-30
Every few weeks when I boot I get a message some like this: "Checking disk integrity please wait. This could take some time." But then it finishes in about 2 seconds. Also, I have three drives, two internal and one external USB, all pretty large, and it clearly isn't checking more than one but I don't know which one. So my questions are... What program is being run to do that check? Can I run it manually? Is there a configuration file somewhere that I can change to make it check all drives and check them more thoroughly? Is there a log that shows the results of the check?

This is Ubuntu 10.04 on a Dell Optiplex desktop machine. On Ubuntu 9.04 the same utility would run occasionally but it would take several minutes, maybe more.

---

### Post by prodigy_ on 2010-07-30
Yes, you can check file systems manually with **fsck** command. But the reason why it exits so fast on scheduled checks is probably that all file systems are marked as "clean" (this means no check is necessary).

---

### Post by RobertL on 2010-07-31
Thanks for explaining that. I just spent the last hour trying to figure out fsck's configuration. It looks like it is yet another thing that was trashed by the upgrade from 9.04 to 10.04. 

I thought I cleaned up all the messes the upgrade made but this looks like another one. I'm not clear on everything, but one thing I see that's wrong is that my external 1GB drive, which I use all the time and is normally mounted, is marked as swap in /etc/fstab. I think it was probably used by the upgrade process for swapping and was just left that way. 

The upgrade mischaracterised my variouis drives, which caused serious problems. Like it went ahead and partitioned my external drive and then installed the new linux on one of the partitions even though my hardware can't boot from it.  I didn't want the space to be split because I relied on the huge disk space for backups. I tried to delete one of the partitions it made and grow the other partition into the space but that caused another problem so I've lost half of my drive. Now I don't want to change anything else for fear of making things worse. 

Linux isn't supposed to have problems like this!!!

---

### Post by prodigy_ on 2010-07-31
Sorry to hear about your upgrade experience, mine wasn't much better.

You might want to try Boot Info Script linked in my sig. Normally it's used to diagnose boot issues, but it also outputs a lot of useful info about hard drives and partitions.

Post the results here and we'll see what can be done to recover your previous partitioning scheme. Particularly, having swap partition on an external drive isn't a good thing. Need to move it to a more suitable location.

---

