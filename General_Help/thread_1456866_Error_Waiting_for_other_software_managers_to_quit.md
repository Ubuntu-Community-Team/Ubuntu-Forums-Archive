---
title: "Error Waiting for other software managers to quit"
date: 2010-04-17
forum: General Help
---

### Post by noelia on 2010-04-17
Hi! I'm new on Ubuntu and while I was trying to download some software the following error appears; Waiting for other software managers to quit, I just read that the solution is to run manually
 'sudo dpkg --configure -a' Anybody please tell me exactly where I do this, please I need exact instructions
(Computer Dummy) I would really appreciate your help.

---

### Post by dcstar on 2010-04-17
> **noelia said:**
> Hi! I'm new on Ubuntu and while I was trying to download some software the following error appears; Waiting for other software managers to quit, I just read that the solution is to run manually
 'sudo dpkg --configure -a' Anybody please tell me exactly where I do this, please I need exact instructions
(Computer Dummy) I would really appreciate your help.

When you first boot up Ubuntu each day a process automatically runs (after 5 minutes) to check for any software updates and then download and install them.

If you happen to try and install software at the same time then you can have issues like this. Usually if you wait a few minutes and try again things then work ok.

If you also have multiple software installation packages open at the same time you can also have this sort of issue - you should only have one single method of installing software running at any one time.

---

