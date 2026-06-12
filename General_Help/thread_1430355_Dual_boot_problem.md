---
title: "Dual boot problem"
date: 2010-03-15
forum: General Help
---

### Post by zikomo on 2010-03-15
Help!!.
I have Ubuntu 9.1 installed as DUAL BOOT with Windows XP.
Ubuntu boots up and works just fine.
However,although Windows is in the Boot List[Windows Xp(on/dev/sda1)]I cannot boot into Windows.
I get a blank screen and am required to reboot back into Ubuntu.
This is very puzzling[and distressing!]
All suggestions will be gratefully received.Oh,that I knew more.
Rgds.

---

### Post by chinagirl_yingying on 2010-03-15
haha,a am a chinese girl !hello!

---

### Post by john newbuntu on 2010-03-15
It could be that the partition boot sector of windows is bad.  Fix the windows XP problem first by using the recovery console in your XP CD.  Run the command "fixboot C:".
Once windows is ok, fix the Ubuntu boot problem by following step 13 from the following post.  You need to use the Karmic liveCD to do this:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

