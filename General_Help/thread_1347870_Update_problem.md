---
title: "Update problem"
date: 2009-12-06
forum: General Help
---

### Post by notesetter on 2009-12-06
I had a hard kernel panic during updates and lost gdm. I did ```
sudo apt-get --configure -a
``` and everything appeared fine until I rebooted. When I rebooted, I was dropped into a root shell. I was able to start the Xorg server by doing ```
startx
```, but I was logged in as root instead of my regular user account. I opened a terminal and did ```
apt-get install --reinstall gdm
``` and now I have a regular graphical login. I'm now having problems shutting down and I think it's related to packages which were being updated during the freeze and are hence broken. Is there a way to determine which packages were last updated so that I may ```
sudo apt-get install --reinstall
``` them? A log?

This happened on a Compaq Presario 2170 Laptop running Ubuntu Studio 9.10. I have occasionally had problems with kernel panic, but this is the first time it's happened during an update.

Thanks in advance,

David

---

