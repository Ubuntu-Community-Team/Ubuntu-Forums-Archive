---
title: "Problems with Autoconf using gcc 3.4"
date: 2006-03-27
forum: General Help
---

### Post by neilp85 on 2006-03-27
When Autoconf does it's checks for g++, etc... on my computer it says it can't find them: 

checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no

I use version 3.4 of gcc rather than 4.0 due problems I've had compiling older projects with 4.0.  I believe this is what's causing the problem.  I checked the log file and one of the paths Autoconf checks is where all the above executables reside.  The only difference is everthing is appended with -3.4.  My old fix for this was just setting alias g++='g++-3.4' in .bashrc.  Now it appears I need a better way of fixing this so that everything recognizes version 3.4 of gcc as my default compiler.

---

