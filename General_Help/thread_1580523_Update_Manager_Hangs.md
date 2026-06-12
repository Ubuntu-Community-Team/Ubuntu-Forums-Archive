---
title: "Update Manager Hangs"
date: 2010-09-23
forum: General Help
---

### Post by Cybrmerc on 2010-09-23
Recently I've been having trouble updating my ubuntu 10.04 system. When I run update manager it will hang during the "downloading packaging information" window until I 'force quit' the 'gksu' process (which is in a state of pipe_wait). A few times update manager has frozen, in turn causing a widespread freeze of all my other windows and my system - in which my only option is doing a cold reboot. Really strange....any help?

---

### Post by rgiles43 on 2010-09-23
Hello,

Have you tried running the updates manually through the command line via:

sudo apt-get install updates?

Hope this helps.

---

