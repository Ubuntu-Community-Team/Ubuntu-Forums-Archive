---
title: "Boot straight to tty1?"
date: 2012-01-22
forum: General Help
---

### Post by Loser777 on 2012-01-22
I'm running an Ubuntu 11.10 minimal install without gdm or kdm installed. However, I boot the system, it goes to tty7 and I have to use alt + arrow key to switch to tty1 in order to login. I've tried the vt.handoff fix described @ [http://ubuntuforums.org/showpost.php?p=11207776&postcount=6](http://ubuntuforums.org/showpost.php?p=11207776&postcount=6) by setting vt.handoff = 1 and by commenting the line out completely. Nothing seems to work.

---

### Post by Loser777 on 2012-01-22
EDIT: It seemed that because the the condition in the line above was "splash" and my grub default was set to quiet splash all I had to do was change the line to so that "$word" = "quiet splash". and set vt.handoff=1.

---

