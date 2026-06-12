---
title: "Won't boot after hard shut down"
date: 2012-09-17
forum: General Help
---

### Post by xeitgeixt on 2012-09-17
So I was in a rush and Ubuntu wanted to run a hard-disk scan. The screen informed me that I could press 'c' and hence skip the whole process. I did. 

Unfortunately at this point I got a blank screen- so I did what I had to do, I performed a hard shut down. 

Now Ubuntu will not boot. All I get is the off-purple colored screen sitting there doing nothing. 

Any advice?

---

### Post by oldfred on 2012-09-17
Never do a hard shutdown, unless the elephants do not work.

Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
Another
sudo init 0

Generally pressing and holding Ctrl+Alt and
then PrintScr, R, E, I, S, U, B (Raising Elephants Is So Utterly Boring)
should do a clean reboot.
R gives back control of the keyboard, S issues a sync, E sends all processes but init the term singal, I sends all processes but init the kill signal, U mounts all filesystem ro to prevent a fsck at reboot, B reboots the system


Now you probably have to run a full filecheck from a liveCD.

#From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by xeitgeixt on 2012-09-20
The method above did me no good unfortunately. Before I go head and reinstall Ubuntu, does anyone else have any suggestions?

---

