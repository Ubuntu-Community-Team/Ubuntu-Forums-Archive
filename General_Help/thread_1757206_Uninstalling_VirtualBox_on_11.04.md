---
title: "Uninstalling VirtualBox on 11.04"
date: 2011-05-13
forum: General Help
---

### Post by jezzyjez on 2011-05-13
I am running 11.04 and am trying to upgrade my VBox, when trying to uninstall i am having problems.It doesn't show as installed in Synaptic and when trying apt-get remove tabbing 'V' doesn't bring up virtualbox

Any ideas?

Thanks 
Jez

---

### Post by Toz on 2011-05-13
What does:```
dpkg -l | grep -i virtualbox
``` return?

---

### Post by jezzyjez on 2011-05-13
It returns

Usage: grep [OPTION]... PATTERN [FILE]...
Try `grep --help' for more information.

---

### Post by jezzyjez on 2011-05-13
Tried again using capitals on VirtualBox and it returns nothing

---

### Post by Toz on 2011-05-13
Try it again - it should not give an error.```
dpkg -l | grep -i virtualbox
``` 

Copy everything from the terminal back here, including the command.

How did you install the original virtualbox?

---

### Post by jezzyjez on 2011-05-13
It returns nothing, just continues onto the next line of terminal waiting for command.

I installed it from the Virtualbox website, I think it was a .DEB file

---

### Post by Toz on 2011-05-13
Okay then, post back, in quote tags, the whole contents of:```
dpkg -l
```If it's easier, you can redirect the output to a file and copy/paste from that file:```
dpkg -l > dpkg.listing
```If you've installed from debs, its gotta be there.

---

