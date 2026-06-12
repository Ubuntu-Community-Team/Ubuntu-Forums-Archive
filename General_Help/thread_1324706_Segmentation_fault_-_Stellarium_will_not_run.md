---
title: "Segmentation fault - Stellarium will not run"
date: 2009-11-12
forum: General Help
---

### Post by Andy H. on 2009-11-12
I'm new to Linux, did a clean install of 9.04 and upgrade to 9.10.   In hopes of learning more about how to use Linux, download software, and enjoy a hobby I have downloaded and installed Stellarium.  I've got the program installed as indicated by presence in the "Applications" list, however it won't run from launcher or in terminal mode.

Attempting to run "stellarium" in terminal mode returns the following:

> QProcess: Destroyed while process is still running.
 ------------------------------------------------------- 
[ This is Stellarium 0.10.2 - [http://www.stellarium.org]("http://www.stellarium.org/") ] 
[ Copyright (C) 2000-2009 Fabien Chereau et al          ] 
 ------------------------------------------------------- 
Writing log file to: "/home/andy/.stellarium/log.txt" 
File search paths: 
  0 .  "/home/andy/.stellarium" 
  1 .  "/usr/share/stellarium" 
Config file is:  "/home/andy/.stellarium/config.ini" 
Segmentation fault
What is a Segmentation fault and how do I fix this?

Any help would be greatly appreciated.

Thanks,

  -AH

---

### Post by ranch hand on 2009-11-12
There seems to be a problem with that app.  What you should do is, with stellarium running, open a terminal and type"
```

ubuntu-bug stellarium

```
You will need to set up a launchpad account.

---

### Post by Andy H. on 2009-11-12
Thanks! I've got info waiting to send to the developers.  setting up Launchpad now.

---

### Post by Adam A on 2010-01-03
I've been having the same problem - Stellarium crashes with a segmentation fault on startup (on Xubuntu 9.10).

For anyone else having the same problem, here's the link to the bug on launchpad:

[https://bugs.launchpad.net/ubuntu/+source/stellarium/+bug/481669](https://bugs.launchpad.net/ubuntu/+source/stellarium/+bug/481669)

---

### Post by ichthyostega on 2010-08-26
same problem here. Segfault right at start :-/
(Ubuntu Lucid, Laptop with AMD mobility radeon X1500)

damn... I liked Stellarium and now this disappointment after the upgrade from Hardy ;-)

---

