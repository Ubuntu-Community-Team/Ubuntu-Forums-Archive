---
title: "Nethack Qt launch problem"
date: 2009-10-14
forum: General Help
---

### Post by Aonshix on 2009-10-14
Hello, and I apologise in advance for what is probably a simple issue, I'm completely unfamiliar with linux troubleshooting :(

I'm running UNR 9.10 beta with the latest updates and it's pretty sweet, however my copy of nethack has stopped launching yesterday, after about 8 days of working flawlessly. I first tried sudo apt-get removing and installing QT again, but that didn't fix the problem. I figured I'd try to start the game through terminal in order to get more information about what happens, and this was the result:

"QSettings::sync: failed to open '/home/ewan/.qt/qt_plugins_3.3rc.tmp' for writing

QSettings::sync: failed to open '/home/ewan/.qt/qt_plugins_3.3rc.tmp' for writing
Waiting for access to /var/games/nethack/perm.  (9 retries left).

Waiting for access to /var/games/nethack/perm.  (0 retries left).
I give up.  Sorry.
Perhaps there is an old /var/games/nethack/perm_lock around?"


Duplicate lines omitted. As far as I know I haven't done anything to the game except running it and have made no system changes recently except installing SCUMMVM.  

Thanks for your time.

-Aon

PS: How funny is the 'I give up' line ><

---

### Post by exline on 2009-11-01
I am having a similar problem after upgrading Xubuntu from 9.04 to 9.10.  In my case, QT Nethack starts, but the graphics are completely scrambled (almost like the resolution was way off, and you just get a bunch of thin lines).  Fortunately, it does respond and I was able to resave my game.
 
Any ideas?  Thanks!

---

