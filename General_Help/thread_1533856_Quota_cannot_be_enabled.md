---
title: "Quota cannot be enabled"
date: 2010-07-18
forum: General Help
---

### Post by ygoe on 2010-07-18
I tried to enable quota support on Ubuntu 10.4 Server. I have installed the packages quota and quotatool, updated /etc/fstab to include the usrquota option on /, rebooted and ran the following command:

$ sudo quotacheck -acmu
quotacheck: lstat Cannot stat `//home/****/.gvfs': Permission denied
Guess you'd better run fsck first !
exiting...

As you can see from its output, it's quite uncooperative. The directory in question is dr-x------ by me, thus is think it may be inaccessible by root. This is the first stop, I don't know how many would follow if I (erroneously) change this.

(This is the second post about the issue because a moderator closed the other one I replied to. Sometimes they say "don't open a second thread", then they say "now that one was too old"...)

---

