---
title: "Found a bug in the installation of Wubi!"
date: 2010-05-05
forum: General Help
---

### Post by lawpetv on 2010-05-05
Okay sorry guys im new and I don't know where to submit bugs for Wubi.


I found this bug to be consistent in all 9.04,9.10,10.04.


Here's the problem:
On Windows XP, after installing Ubuntu with wubi, at restart the screen where you get to choose between Windows and Ubuntu doesn't show up. It boots straight to Windows XP.



Turns out:
turns out that when wubi edited the boot.ini, it somehow added a ";" before "timeout".
so i deleted that ";" and it totally works now.

---

### Post by blueridgedog on 2010-05-05
See this page for learning how to report bugs:

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

