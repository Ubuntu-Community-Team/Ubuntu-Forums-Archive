---
title: "Amarok won't load"
date: 2009-11-30
forum: General Help
---

### Post by bmdaily on 2009-11-30
While I am very much a beginner with Linux, I have been running it for a few years. I recently updated my Kubuntu box to the newest version (9.10 right?) and it was a fairly flawless upgrade but now Amarok doesn't work. I'm running version 1.4 (not a big fan of Amarok 2) and every time I attempt to open it, I get this: 

Amarok could not find any sound-engine plugins. Amarok is now updating the KDE configuration database. Please wait a couple of minutes, then restart Amarok.
If this does not help, it is likely that Amarok is installed under the wrong prefix, please fix your installation using:
$ cd /path/to/amarok/source-code/
$ su -c "make uninstall"
$ ./configure --prefix=`kde-config --prefix` && su -c "make install"
$ kbuildsycoca
$ amarok
More information can be found in the README file. For further assistance join us at #amarok on irc.freenode.net.


I've been browsing the web for a solution for a few days now without any luck. I was wondering if anyone had a solution to this or had any ideas on how to fix it. Thanks for your help.

---

### Post by Zorael on 2009-11-30
Much like it suggests, I'd try #amarok on irc.freenode.net. There's also [a few PPAs](https://launchpad.net/ubuntu/+ppas?name_filter=amarok+1.4) with Karmic packages of Amarok 1.4. Perhaps in Karmic 1.4 needs a fix to work, that those packages contain?

---

