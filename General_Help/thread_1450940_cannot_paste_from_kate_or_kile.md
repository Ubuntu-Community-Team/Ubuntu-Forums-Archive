---
title: "cannot paste from kate or kile"
date: 2010-04-09
forum: General Help
---

### Post by formerwindowspoweruser on 2010-04-09
When I am using kile or kate text editors, everything works fine except pasting text into a different editor. For example, if I highlight text in kate, then right click "copy" and right click "paste" in the Firefox URL or paste into a gedit file or vi, the "paste" option is grayed out. Similarly if I highlight in kate or kile and attempt to use the middle mouse button.

I can copy paste within a kate document, or multiple documents in a session, but I cannot copy/paste across multiple sessions. I am also unable to copy from kate and paste into kile.

I am able to copy from firefox/nautilus/gedit then paste into both kate and kile. 

I know this used to work (copy-paste between editors), so I suspect that an update caused the problem. However, I don't see any open bug reports or other instances on the forums here.

My goal is to be able to copy-paste using both ctrl-c/ctrl-v and the middle mouse button between multiple editors. Currently, only gedit-->kate works, whereas I would like to have gedit<-->kate

version information:

$ kate -v
Qt: 4.5.2
KDE: 4.3.2 (KDE 4.3.2)
Kate: 3.3.2
$ kile -v
Qt: 4.5.2
KDE: 4.3.2 (KDE 4.3.2)
Kile: 2.0.83
$ gedit --version
gedit - Version 2.28.0
$ uname -a
Linux ben-desktop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux

I just ran 
apt-get update
apt-get upgrade

Ubuntu 9.10

Please let me know if more information is needed.

---

### Post by formerwindowspoweruser on 2010-04-18
As of April 16 2010, copy-paste from kate and kile to gedit or firefox is working again, after an update.

Cause unknown, but problem resolved.

---

