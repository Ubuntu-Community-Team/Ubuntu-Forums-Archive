---
title: "Making an sh script run on logout..."
date: 2011-07-21
forum: General Help
---

### Post by waveOSBeta on 2011-07-21
I'm trying to make a sh script that will kill a program on logout. The issue is, all I know how to do with launching an sh file is making it run on login. HElp would be greatly appreciated.

---

### Post by UCSBGauchosRock on 2011-07-22
Hmmm interesting situation. I did a little bit of googling and I found this webpage that might be of some use for you. I have never personally needed to run an sh script at logout although firefox has that annoying problem of not closing "firefox-bin" and appearing as a nonresponsive program upon shutdown, restart, or logout.

EDIT: Oops forgot to add the webpage; sorry about that: [http://www.webrichsoftware.com/?p=20](http://www.webrichsoftware.com/?p=20)

---

### Post by waveOSBeta on 2011-07-22
> **UCSBGauchosRock said:**
> Hmmm interesting situation. I did a little bit of googling and I found this webpage that might be of some use for you. I have never personally needed to run an sh script at logout although firefox has that annoying problem of not closing "firefox-bin" and appearing as a nonresponsive program upon shutdown, restart, or logout.

EDIT: Oops forgot to add the webpage; sorry about that: [http://www.webrichsoftware.com/?p=20](http://www.webrichsoftware.com/?p=20)
Thanks! :D

I'm making a minimal enviorment in my login screen and need to kill network manager.

---

### Post by btindie on 2011-07-22
That method won't actually work to run a script when a user logs out, it'll only work if the system is shutdown.

There's the file ~/.bash_logout which can be used for console sessions but I don't think it would be of use in your case. I've also read that it may be possible using DBus to get a message that the session is ending.

I also found this thread [http://ubuntuforums.org/showthread.php?t=252935](http://ubuntuforums.org/showthread.php?t=252935) which mentions a fairly straight forward method of running a script at logout.

---

### Post by Redsandro on 2011-07-22
I'm not entirely sure but take a look at:

/etc/gdm/PostLogin/Default

I use it to kill my synergy sessions.

---

