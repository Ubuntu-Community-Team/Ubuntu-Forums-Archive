---
title: "cleaning up packages"
date: 2010-12-16
forum: General Help
---

### Post by pokeyThePenguin on 2010-12-16
I've had Ubuntu on my computer for a few years now, and during that time, I've installed and uninstalled a lot of different packages. I'm in the mood for doing some cleaning up.

I ran "dpkg --get-selections," and this showed some packages flagged as "deinstall." I read that this means that the package has been removed, but not purged, which I guess means the configuration files are still around. Will running dpkg -P on all those packages be safe?

For future reference, is dpkg -P more thorough than apt-get purge?

There's also a lot of hidden directories in my home folder. Is there a good, safe way to clean up that mess too?

---

### Post by Hoopz on 2010-12-16
you can try sudo apt-get autoremove that will help.  This thread is also a big help for me.   [http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

---

