---
title: "Setting EDITOR=emacs causes lockup"
date: 2010-01-12
forum: General Help
---

### Post by Azguz Bloodfist on 2010-01-12
Hi,

I'm putty'd into an Ubuntu server box and have **EDITOR=emacs** set. However whenever I run **crontab -e** my shell locks up.

I can use emacs normally by typing **emacs **from the command line, so I'm not sure what problem is. If I set **EDITOR=vi** I can run **crontab -e** and it opens in vi (which isn't a solution...)

Any advice?

---

### Post by iponeverything on 2010-01-12
you might try starting it with -nw option or it might have to do with the terminal emulation that putty is using..

---

### Post by Azguz Bloodfist on 2010-01-20
Thanks, adding that option seemed to work :D

---

