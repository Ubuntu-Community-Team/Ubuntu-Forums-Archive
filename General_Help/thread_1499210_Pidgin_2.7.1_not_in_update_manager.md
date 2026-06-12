---
title: "Pidgin 2.7.1 not in update manager"
date: 2010-06-01
forum: General Help
---

### Post by altjx on 2010-06-01
There's a new version of Pidgin on the pidgin website but it's not available in the update manager. I've tried checking for updates but nothing...

Any idea how to install the update? I have downloaded the source from the site "pidgin-2.7.1.tar.bz2" but no idea how to install it. None of the "make" "make install" "sudo make install" or any of that sort works. Need help

---

### Post by altjx on 2010-06-01
or how would i be able to install a tar.bz2 file?

---

### Post by Yaldair on 2010-06-02
I installed it this way:[ http://ubuntuforums.org/showthread.php?t=613049]("http://ubuntuforums.org/showthread.php?t=613049")

Just followed the first post, excepting the purge since I already removed everything.

However, I think something went wrong with my checkinstall, so I'm not sure how the removal will go later on.

When I use the plugin that checks for new versions, it does say there is a new version though. Almost like I installed an older version (compared to the one you get through update manager). But the one I installed that way kept crashing randomly which is the reason why I compiled it from source.

Anyway, hope this helps.

---

### Post by Soul-Sing on 2010-06-02
pff add the pidgin repos./source via launchpad: [https://launchpad.net/~pidgin-developers/+archive/ppa](https://launchpad.net/~pidgin-developers/+archive/ppa)
and you get the newest version.

---

