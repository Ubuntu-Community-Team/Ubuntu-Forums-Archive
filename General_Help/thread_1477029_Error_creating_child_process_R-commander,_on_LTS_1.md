---
title: "Error creating child process R-commander, on LTS 10.4"
date: 2010-05-08
forum: General Help
---

### Post by zombie_jesus on 2010-05-08
Well, I work with social sciences and I really need to use "R". R is a program used for statistics and it has a module called R-commander, which let things easier to deal and comes with several options as opening SPSS files (another statistical package commonly used by Windows users) and other things. THe problem is, as Rcmdr is a module for R, when I run it, it opens a terminal window and then he runs the module, which opens a friendly gui. 

It worked okay and clean in Ubuntu 9.10, but for LTS 10.4 I keep getting an error, no matter I reinstall the modules or the entire program. I even installed Ubuntu again without upgrading it from karmic Koala. But there is the same error msg.

The error message says:

"Error while creating a child process for this terminal". The strange part is there is no other msgs in the terminal or errorlogs. I would appreciate any help. I really need to use this software for work.

hugs to ye all.

Zombie_jesus blessings for all. :guitar:

---

### Post by al347721 on 2010-05-08
chmod a+x /usr/lib/R/site-library/Rcmdr/etc/linux/Rcmdr.sh

This worked for me. More info at [http://www.mail-archive.com/debian-bugs-closed@lists.debian.org/msg276470.html](http://www.mail-archive.com/debian-bugs-closed@lists.debian.org/msg276470.html)

Ubuntu 10.04 LTS amd64

---

### Post by stimpak on 2010-05-20
cheers that solved the problem.

I'll file a bug at ubuntu bugs for it

---

### Post by CyberBob on 2010-08-30
Thanks! Fixed it on my system too!!

---

