---
title: "Can't run Ubuntu Software center and something more"
date: 2011-01-09
forum: General Help
---

### Post by gammymix on 2011-01-09
Hi, I have just installed Ubuntu 10.10 and I can't get Ubuntu Software center running. I opet it, it get's minimized and then it's gone. I saw some help and solutions on the forum but it didn't work, any ideas?
Also I have downloaded a .deb file, Google Chrome and I can't install it. I am new at Linux, so any help or ideas? :)

---

### Post by TeoBigusGeekus on 2011-01-09
Open software center from command line
```
software-center
```
and post any error messages.

The same applies to chrome. Try to install from command line with
```
sudo dpkg -i packagename.deb
```
and post the messages you get.

---

### Post by LewRockwellFAN on 2011-01-09
If that doesn't help it doesn't take long to try uninstalling it and then reinstall it with Synaptic. Might be worth a try.

---

