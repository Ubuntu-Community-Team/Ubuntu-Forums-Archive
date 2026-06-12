---
title: "problem to add windowas xp to grub loading"
date: 2010-03-28
forum: General Help
---

### Post by pooya_mr2009 on 2010-03-28
hi every body.
1 day ago my grub destroyed!
i reinstall it but just one of my ubuntu came.
by the way i have 5 ubuntu 9.10 and 1 windows xp.
how can i add my windows xp to grub loading?
thank a lot.
bye!

---

### Post by r_s on 2010-03-28
5 ubuntu karmic...omg.
try sudo update-grub.. it should find all your partitions.

---

### Post by oldfred on 2010-03-28
If you installed karmic from liveCD not an upgrade you have grub2 and it is just showing the updates to the kernels.

You can remove old kernel but have to be careful not to remove the one you are using. We also suggest keeping one old one so you have a backup in case the new one has issues.

includes line to limit display to two does not uninstall them.
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)

In synaptic search for linux-image to choose to delete old ones
Also command line in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

---

