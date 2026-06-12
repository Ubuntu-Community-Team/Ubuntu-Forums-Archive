---
title: "Opening a Lock file"
date: 2006-03-20
forum: General Help
---

### Post by zdwc01 on 2006-03-20
Had ubuntu, wanted to change to kubuntu. Did sudo apt-get install kubuntu-desktop. Got msg 'Could not open lock file /var/lib/apt/lists/lock-open (13 Permission denied) unable to Lock the list directory. What now can I do to install Kubuntu. Thks.

---

### Post by mlind on 2006-03-20
Some other process has already "locked" the update process.

Do you have Synaptic or other update mangers running simultaneously?
You have to close the others before doing apt-get from command-line.

And you must use ***sudo** apt-get ....*

---

