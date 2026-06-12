---
title: "Problem with keepassx and system tray"
date: 2011-11-07
forum: General Help
---

### Post by BarnOwl on 2011-11-07
I have used keepass for a some time.  I recently upgraded to ubuntu 11.10 with a clean install and I installed it from the software center.  I figured out how to set my whitelist to 'all' and set it to go into the tray.  The icon shows up there as it should but, once I shrink it there, I can't expand it.  I can lock it and unlock it but, it never expands.  The only other option I have is to quit.

This is a minor problem but, it's irritating.

---

### Post by gurgelsmurf on 2013-03-11
Sorry to resurrect this old thread, but I had the same problem and just wanted to share the solution to help others.
There is a bug report for this in launchpad: [https://bugs.launchpad.net/ubuntu/+source/keepassx/+bug/842224](https://bugs.launchpad.net/ubuntu/+source/keepassx/+bug/842224)  
But at least in my Ubuntu installation the sni-qt.conf file is in a different location, /etc/xdg/sni-qt.conf

Solution:

Sudo gedit /etc/xdg/sni-qt.conf
Add this: keepassx=1
Save and restart Keepassx

---

