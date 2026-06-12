---
title: "Ctrl+C shows in terminal in karmic"
date: 2009-11-03
forum: General Help
---

### Post by ChaoticMind on 2009-11-03
I noticed that when you hit Ctrl+C in gnome-terminal in Ubuntu 9.10 (Karmic Koala), it actually displays it. Previous behaviour was simply to jump to a new line and abort the current one. 

I am fond of the old behaviour, any ideas how to revert back to it?

---

### Post by mdw on 2009-11-04
I have noticed that too.

"stty -ctlecho" switches this behaviour off. Put it into .bashrc or somewhere.

--
mdw

---

### Post by ChaoticMind on 2009-11-08
Thanks, that worked great.

---

