---
title: "apt-get remove emacs"
date: 2011-08-03
forum: General Help
---

### Post by nmaster on 2011-08-03
when i try in remove emacs22, the emacs-snapshot is installed.  then when i try to remove emacs-snapshot, emacs22 is installed.

same thing happens when i use purge instead of remove

someone please save me from the circle of wasted time...
```

neal@neal-Thinkpad:/home/neal 
$ sudo apt-get remove emacs22
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  emacs-snapshot emacs-snapshot-bin-common emacs-snapshot-common
Suggested packages:
  emacs-snapshot-el
The following packages will be REMOVED:
  emacs22
The following NEW packages will be installed:
  emacs-snapshot emacs-snapshot-bin-common emacs-snapshot-common
0 upgraded, 3 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B/18.3MB of archives.
After this operation, 70.4MB of additional disk space will be used.
Do you want to continue [Y/n]?

```

EDIT:
so i didn't actually solve the problem that i described, but i actually didn't properly describe my problem ;)
what i really wanted to do was remove emacs22 so i could install emacs22-nox.  i just needed to install the nox package first and then remove emacs22

the problems arose when i had gotten excited about zile (even smaller than vim!) and prematurely decided to remove emacs.

---

