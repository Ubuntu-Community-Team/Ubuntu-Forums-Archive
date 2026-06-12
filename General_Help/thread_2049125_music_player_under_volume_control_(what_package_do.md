---
title: "music player under volume control (what package does that?)"
date: 2012-08-27
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2012-08-27
at 1st i had play/pause controls under my volume icon, i don't really need it but it is bugging me that i can seem to get it back
i had been installing some stuff and removed some things (mostly stuff i some how installed without noticing like rhythmbox/nautilus/brasio)
i am using gmusicbrowser on xububtu 12.04 with xfce 4.10

---

### Post by Toz on 2012-08-28
Make sure you have the **indicator-sound-gtk2** package installed and an mpris-compatible player (of which gmusicbrowser is one).

---

### Post by pqwoerituytrueiwoq on 2012-08-28
```
sudo apt-get install indicator-sound-gtk2
[sudo] password for chad: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
indicator-sound-gtk2 is already the newest version.
The following packages were automatically installed and are no longer required:
  libgtksourceview-3.0-0 gir1.2-gtksource-3.0 libgtksourceview-3.0-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.
```does it not work on xfce 4.10?
** the 11 not upgraded are a old version of compiz that does not have the flickering when moving windows from between workspaces
edit:
[IMG]http://i.imgur.com/88zzr.png[/IMG]

---

