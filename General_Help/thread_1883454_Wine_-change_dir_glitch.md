---
title: "Wine -change dir glitch?"
date: 2011-11-19
forum: General Help
---

### Post by poodoopealeoap on 2011-11-19
Every time i try to install anything in wine, ever since I upgraded to 11.04, I can't because I get a message that says "wine fatal error -change dir". I've completely uninstalled wine, done "sudo apt-get autoremove" and reinstalled from USC, but I still have the same problem.....

SOMEONE HELP!

---

### Post by jjex22 on 2011-11-19
Hi there, I suspect you need to purge out the config files too.

bacially going to quote the man page here, but when removing software in ubuntu it goes a little like this

_apt-get remove packagename_
This uninstalls the package, but leaves the config files.

_apt-get purge packagename_ 
This does the same thing, but additionally goes after the config files - we have to two commands as sometimes you'd like to keep them! you usually run one or the other.

_apt-get autoremove _ 
This then takes out packages that have been installed because other pakages needed them (dependencies) but you no longer need them on your system.


Another helpful little trick is to run 'sudo apt-get autoclean' from time to time - this is like windows clean up tempory files for package manager.

---

### Post by poodoopealeoap on 2011-11-22
I tried removing, purging, cleaning and whatever else you can do to completely get rid of everything before a reinstall. It didn't work... but did find out how to get plants vs zombies to install. Just select it in winetricks and bam.. done.

---

