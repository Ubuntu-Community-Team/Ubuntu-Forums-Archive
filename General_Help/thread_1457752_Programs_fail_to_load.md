---
title: "Programs fail to load"
date: 2010-04-19
forum: General Help
---

### Post by bo. on 2010-04-19
Just installed Ubuntu for the first time on my dell laptop and when i click on Ubuntu Software center or Update Manager they dont load up.  Anyone know whats goin on?

---

### Post by benson444 on 2010-04-19
It could be that the update-manager is already running in the background. One of the programs in System->Preferences->Startup Applications is update-notifier. Only one package manager app can run at any one time.

Try running update-manager or software-center in a terminal and see what output you get.

---

