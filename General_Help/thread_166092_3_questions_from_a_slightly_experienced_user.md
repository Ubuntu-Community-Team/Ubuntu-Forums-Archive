---
title: "3 questions from a slightly experienced user"
date: 2006-04-25
forum: General Help
---

### Post by ModusOperandi on 2006-04-25
1) I don't know how to upgrade to KDE 3.51. I recall a thread on here a while back, but I can't look back into my own posting history, so I can't find it.

2) How do I change the dpi setting? The fonts are too big for my liking.

3) How would I go about adding support for an extended desktop. My monitors will be running at different resolutions.

TIA

---

### Post by rado_london on 2006-04-25
to change the font go to System - Font and change the size and the type of font. For the monitor you have to edit xorg.conf I dont know how so make a search around the forum. I am not familiar with KDE so i cant answer the upgrade question.

Good luck

---

### Post by Sef on 2006-04-25
> 1) I don't know how to upgrade to KDE 3.51. I recall a thread on here a while back, but I can't look back into my own posting history, so I can't find it.

check out the link below.

[http://kde.org/]("http://kde.org/")

---

### Post by gingermark on 2006-04-26
[QUOTE=ModusOperandi]1) I don't know how to upgrade to KDE 3.51. I recall a thread on here a while back, but I can't look back into my own posting history, so I can't find it.[/QUOTE]
Kubuntu.org has provided packages.
Add the following to your sources.list:
deb [http://kubuntu.org/packages/kde35](http://kubuntu.org/packages/kde35) breezy main
deb [http://kubuntu.org/packages/kde351](http://kubuntu.org/packages/kde351) breezy main

(and if you fancy going to 3.5.2)
deb [http://kubuntu.org/packages/kde352](http://kubuntu.org/packages/kde352) breezy main

Some people have had problems, but as long as both (or all three) repositories have been added, and you "sudo apt-get **dist**-upgrade" you should be fine.

---

