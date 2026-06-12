---
title: "Upgrade"
date: 2006-05-13
forum: General Help
---

### Post by sinkxdie on 2006-05-13
If i upgrade using 

gksudo "update-manager -d"

or even just doing the manual

apt-get update
apt-get dist upgrade

will i lose my KDE setup? I know that I would keep my Gnome setup but I dont know about my KDE one. 

and by the way, I'm already using Dapper, but I dont know which "flight"

---

### Post by ryanakca on 2006-05-13
You shouldn't loose your kde setup... it'll just update the updateable apps (including the kde ones). I'm running Kubuntu and XFCE and GNOME and AfterStep and all of the other goodies... also, I run this command, so that it upgrades everything (including your window managers), instead of only select apps.

> sudo apt-get update && sudo apt-get dist-upgrade

Cheers,
ryanakca

---

