---
title: "What does LVM do?"
date: 2006-03-26
forum: General Help
---

### Post by Ubuntuud on 2006-03-26
What does LVM do?

---

### Post by Dankitymao on 2006-03-26
LVM (Logical Volume Manager) is a system that allows you to combine several physical hard drives (or partitions) into what appears to the system to be a single continguous device.  For example, in my file server right now I have 2 120GB hard drives and a 240GB hard drive.  Via LVM, Linux sees all 3 drives as a single 480GB drive.  It also allows you to add and remove new drives, and many other things.  It's pretty useful for servers where your storage needs will keep increasing; be warned that the chance of drive failure hosing your storage goes up with each drive that you add, though...backup often! =)

---

### Post by Ubuntuud on 2006-03-26
I only have one harddrive, so of no use to me. Thank you!

---

### Post by grimreaperwithalawnmower on 2006-04-01
Right, I get what LVM is and vaguely how it works (well, enough for me to know that I want to use it) but I can't seem to get anywhere!  I've been using Ubuntu for about 4-5 months now and used beloved Windows before that, so I'm not completely up to speed with all the technicalities yet!

Anyway, here's my situation:  I have 2 80GB hard drives, one with a 22GB partition for Windows (I still need it, regrettably) and the rest is free space.  Now, I want to use LVM to use the rest of the disk space as one "partition" (for want of a better word).  Now, looking on the net, I didn't really find anything particularly helpful with respect to the Ubuntu installer (not that I looked for a huge amount of tme anyway), so I decided to just go for it and formatted away (if I didn't need to, please don't tell me!!!).

Setting up the partitions I have 57GB LVM set up (logical) and then 77.9GB on the other drive to mount to root as an ext3 file system (with 2.1 swap).  When I go to "Configure the LVM" it tells me (when I actually try to set anything up): "No volume groups were found for creating a new logical volume" when I go to Modify LV and something pretty similar in Modify VG.

I've tried numerous combinations and set-ups for the partitions, with the same results each time.

If someone could let me know where I'm going wrong then I'd be immensly greatful!  Cheers in advance!

---

### Post by dcstar on 2006-04-01
[QUOTE=grimreaperwithalawnmower]
......
If someone could let me know where I'm going wrong then I'd be immensly greatful!  Cheers in advance![/QUOTE]
[http://ubuntuforums.org/showthread.php?t=137082](http://ubuntuforums.org/showthread.php?t=137082)

---

