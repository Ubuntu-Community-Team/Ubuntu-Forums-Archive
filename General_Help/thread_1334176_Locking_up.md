---
title: "Locking up"
date: 2009-11-22
forum: General Help
---

### Post by TKleszynski on 2009-11-22
My computer will lock up, won't let me do anything so I will have to shut it off. What can I do to stop this from happening?

---

### Post by Andreas1 on 2009-11-22
first, you could determine if it's xorg, the graphical environment, that locks up. next time it happens, press "alt"+"print screen"+"K", to kill the x server, if it works (=you will be at login again) then you have an [x freeze]("https://wiki.ubuntu.com/X/Troubleshooting/Freeze").

also, if killing the xserver does not work, instead of killing the computer a slightly more gentle way to bring it down would be REISUB:
> Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB will get you safely restarted. REISUO will do a shutdown rather than a restart. had to use it a lot of times myself [recently]("http://ubuntuforums.org/showthread.php?t=1309015").

to fix the issue you should try to find out more about the circumstances in which the system freezes, maybe it's related to a specific application or events like resume from suspend, and so on...

---

