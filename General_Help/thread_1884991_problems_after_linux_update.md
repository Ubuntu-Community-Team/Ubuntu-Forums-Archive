---
title: "problems after linux update"
date: 2011-11-22
forum: General Help
---

### Post by bkbk on 2011-11-22
Lubuntu 11.10: Yesterday, the Update Manager popped up with important security updates to Linux. Since updating, my system has run terribly. After logging in, it takes about 10 minutes for the desktop to load completely (versus a few seconds before the update), and everything runs sluggishly. Also, my hard drive light is on constantly.

Help would be appreciated. Thx.

---

### Post by 2F4U on 2011-11-22
Check the processes that are running in the background with top or htop.

---

### Post by bkbk on 2011-11-22
The computer runs so terribly now that it took me a long time to do this, but I found that lubuntu includes LXTask task manager, so I ran that and managed to take a screenshot with scrot (file attached).

What do I do now? The computer is painfully slow and the hard drive light is on constantly.

---

### Post by bkbk on 2011-11-26
Well, I fixed the problem by reinstalling lubuntu. First, two things that didn't work:
-Selecting the previous version of Linux in GRUB. Same problems as before.
-Reinstalling lubuntu without reformatting the Linux partition of the hard drive. After doing this, the mouse wouldn't work anymore.

Things only worked after reinstalling with a reformat of the Linux partition, then updating lubuntu. Of course, reformatting meant I had to reinstall programs I'd downloaded previously and copy over backed up files, and that was a pain.

---

