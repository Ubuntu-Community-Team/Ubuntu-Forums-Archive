---
title: "error message sudo/also dpkg ????"
date: 2010-06-18
forum: General Help
---

### Post by retro-rocket on 2010-06-18
first of all i could,nt read any attch on my e mails, now i can,t reinstall openoffice sweet, uninstall anything or install i have a message error "sudoapt-getinstall-F" what dose this mean and how do i get. i,ve tried going threw the synaptic package manager now that won,t open, error dpkg i/o also came up, also have 2 broken packages, 
help thanks daz

---

### Post by pastalavista on 2010-06-18
dpkg is the debian package installer and you have one or more that hasn't finished its job. Open a terminal (Applications/Accessories/Terminal) and enter this command
```
sudo dpkg --configure -a && sudo apt-get install -f
``` and then Synaptic and Update manager should work again.

---

