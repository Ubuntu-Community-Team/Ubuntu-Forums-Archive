---
title: "laptop freezes and screen flickers"
date: 2012-09-14
forum: General Help
---

### Post by jopeto on 2012-09-14
I recently did a fresh install of Ubuntu 12.04 on my laptop which has the following specifications:
CPU: Intel Pentium B950
Graphics: Intel Integrated Graphics 2000
Memory: 4GB

Everything works fine, however occasionally the computer freezes (I can still move the mouse, but nothing responds) and the screen starts flickering. The only thing I can do is a hard reboot. I think I am experiencing exactly the same problems as described here:
[http://ubuntuforums.org/showthread.php?t=2051176](http://ubuntuforums.org/showthread.php?t=2051176)

The following suggestions were given there:
1. "look into the system log file if you can find any hint on the crash"
2. "And find out how long it takes for the CPU/Graphics chip to overheat using the later distros."

How do I do these two things?

Also, I found this thread
[http://askubuntu.com/questions/156329/screen-flickering-in-ubuntu-12-04-lts](http://askubuntu.com/questions/156329/screen-flickering-in-ubuntu-12-04-lts)
However doing ```
unity --reset
``` gave me a lot of warnings and errors.

Thanks a lot for your help in advance!

---

### Post by jopeto on 2012-09-14
Just as an update, when the computer freezes and the screen starts flickering, the brightness slidebar also appears as a notification in the upper right corner.
Also, I'm not completely sure about that, but the problem seems to occur predominantly when I'm running on the battery and I leave the computer idle for some time.
Any ideas?

---

### Post by jopeto on 2012-09-17
bump

---

### Post by Elfy on 2012-09-17
*Thread moved to **General Help**.*

---

### Post by jopeto on 2012-09-23
Some further testing shows that maybe this problem is related to the desktop environment used. I get the problem when I'm using GNOME or KDE, but the problem does not exist when I'm using FVWM for example. However still haven't found a solution to the problem. Is it possible that it is some kind of a bug, or just bad configuration on my part?

---

### Post by jopeto on 2012-10-04
bump

---

### Post by jopeto on 2012-12-25
Ended up upgrading to Ubuntu 12.10 and this seems to have fixed the problem.

---

