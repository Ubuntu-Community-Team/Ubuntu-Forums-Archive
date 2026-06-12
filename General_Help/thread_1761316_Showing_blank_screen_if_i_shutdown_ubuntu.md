---
title: "Showing blank screen if i shutdown ubuntu"
date: 2011-05-18
forum: General Help
---

### Post by Linux_buddy on 2011-05-18
When i try to shut down  the computer hangs itself by showing a blank screen, then i have to do forced shutdown by pressing the shutdown key for a long time.why it is so?

---

### Post by Wim Sturkenboom on 2011-05-18
Why? Probably a crash of X
Without proper information, we will never be able to help. Which version of Ubuntu are you using? What hardware; probably mostly interested in the videocard.

You can try to shutdown from a console (as a possible workaround). While in the graphical environment, press <ctrl><alt>x (where x is a number from 1 to 6).
Login with normal username and password and issue the command *sudo shutdown -h now*

You might be able (not sure) to find pointers to the problem in the log files (/var/log/Xorg....).

---

### Post by Wim Sturkenboom on 2011-05-18
PS
Just saw below thread (did not read it); might be of help as it sounds like the same problem

[http://ubuntuforums.org/showthread.php?t=1745593](http://ubuntuforums.org/showthread.php?t=1745593)

---

