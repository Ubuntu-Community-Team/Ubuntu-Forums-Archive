---
title: "Help problem with plymouth?"
date: 2010-08-06
forum: General Help
---

### Post by tnursall on 2010-08-06
I have been using ubuntu for a while now but it has now died and i need help. 
 
I tried a apt-get update and there where packaes i needed so i tried to install them.
Ubuntu then crashed out and stoped responding.
I rebooted and now it only opens a tty with the lines
init: plymouth main process killed by abrt signal
and
init: plymouth-splash main process terminated with status 2.
 
I can login and have tried to apt-get upgrade but i get error 
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
 
I have no internet as dhcp is not working in terminal so an update will not connect to anything.
 
Help please.
 
Thanks Tim

---

### Post by gulabpasha on 2010-09-13
> **tnursall said:**
> I have been using ubuntu for a while now but it has now died and i need help. 
 
I tried a apt-get update and there where packaes i needed so i tried to install them.
Ubuntu then crashed out and stoped responding.
I rebooted and now it only opens a tty with the lines
init: plymouth main process killed by abrt signal
and
init: plymouth-splash main process terminated with status 2.
 
I can login and have tried to apt-get upgrade but i get error 
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
 
I have no internet as dhcp is not working in terminal so an update will not connect to anything.
 
Help please.
 
Thanks Tim
I have the same issue. For me it says (init: plymouth-splash main process (766) terminated with status 1.

Unfortunately this happened to my live ftp server and I'm not sure how to fix it.

I tried booting from single usermod and tried to modify grub but not succeeded.

Please help

Thanks,
Gulab Pasha

---

