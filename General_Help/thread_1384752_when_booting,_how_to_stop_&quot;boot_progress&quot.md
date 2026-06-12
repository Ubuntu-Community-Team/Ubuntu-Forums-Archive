---
title: "when booting, how to stop &quot;boot progress&quot; until mounted raid5 disk is fscked?"
date: 2010-01-18
forum: General Help
---

### Post by guckpup on 2010-01-18
So I have a karmic 64bit install, with a multi-terabyte raid5 array that I have moved /home onto.

Occasionally on reboot (if the machine borks and needs a reset, say) then fsck needs to run (fine, good) - unfortunately the overall boot process continues. This means that the auto-login-to-gnome-X *attempts* to continue, however it can't really continue, since /home isn't mounted.

I get stuff like ice authority errors and so forth - basically it should not move forward (certainly not to running X) *until* the fsck is finished.

Hard to find out how to make this behavior happen... tried looking at the fstab references, trying to find a "hey, if this file system needs checked, chill out on everything else". Didn't find a switch that met the need.

Any ideas how to get the flow described?

G

---

### Post by dfaure on 2010-05-20
Using "1" as the last value in the /etc/fstab line for this partition should do it, I think.

---

