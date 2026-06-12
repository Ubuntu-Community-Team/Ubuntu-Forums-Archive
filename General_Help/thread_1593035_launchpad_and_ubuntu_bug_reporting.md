---
title: "launchpad and *ubuntu bug reporting"
date: 2010-10-11
forum: General Help
---

### Post by dk_zero-cool on 2010-10-11
I am trying to report some xorg/nvidia problems in the new "Final" release of ubuntu 10.10. But it seams that the ubuntu bug reporting system and launchpad contains the same amount of bugs as the new ubuntu release. 

I used to be able to report bugs directly from launchpad, but I am not able to find this option any more. And when I try to use the bug reporting tool in Ubuntu 10.04, it creates and "External drive Error" report when I select a "Display/Xorg" problem. And if I just continue with this report, I get a message at the end that says that the error can't be created, because I don't use Pulse Audio. I do use Pulse Audio, and I don't see what that has to do with my error reporting.

---

### Post by dino99 on 2010-10-11
first step:

- check your repos: synaptic repo tab, you might have only maverick genuine repo activated

- update

- sudo apt-get clean
- sudo apt-get autoclean
- sudo apt-get autoremove
- sudo apt-get install -f
- sudo apt-get dpkg --configure -a

second step:

- check for errors logged into:
a) .xsession-errors (/home, ctrl+h to unhide it)
b) sytem admin logviewer

---

### Post by dk_zero-cool on 2010-10-11
Thanks, now I got the error reporting working. Now I just need a solution for the error I'm reporting :D

---

