---
title: "Trying to get chkrootkit to run"
date: 2012-09-07
forum: General Help
---

### Post by trillen on 2012-09-07
Hi i have been  trying to get this program to run just going in circles

can someone help please ...
out put from term

box@home:~# chkrootkit
The program 'chkrootkit' is currently not installed.  You can install it by typing:
sudo apt-get install chkrootkit
box@home:~# sudo apt-get install chkrootkit
Reading package lists... Done
Building dependency tree       
Reading state information... Done
chkrootkit is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
box@home:~#

---

### Post by Bashing-om on 2012-09-07
trillen ; Hi !

this :  0 to remove and 2 not upgraded. is significant.

might i suggest that you update your package manager ?
```

sudo  apt-get update
sudo apt-get upgrade

```
to upgrade installed packages.

also perhaps, running chkrootkit requires root authority (sudo).

[INDENT]hth <==BDQ
[/INDENT]

---

