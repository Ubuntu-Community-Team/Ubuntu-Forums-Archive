---
title: "Ubuntu 11.10 not booting properly"
date: 2011-12-05
forum: General Help
---

### Post by ramzinjeim on 2011-12-05
Hi everyone i'm new to this forum, i don't consider myself a noob since i've been using ubuntu since version 9.04 but this is the first time a thing like this happens to me.
I have both Windows 7 and Ubuntu 11.10 installed, i have an intel HD GPU and i'm running on a toshiba 775, everything was running perfectly until one time i restarted my computer and selected ubuntu, the normal ubuntu logo and loading appeared, but this time the loading was brief, then a black screen appeared with lines written, i noticed that not every time i get the same lines but in general here's what i get:

* Stopping anac(h)ronistic cron              [OK]
* Starting anac(h)ronistic cron              [OK]
* Stopping cold plug devices                 [OK]
* Stopping log initial device creation       [OK]  * Starting the Windbind daeomon winbind      [OK]
* PulseAudio configured for per-user sessions sand disabled; edit /etc/default/saned [OK]
* Starting CUPS printing spooler/server      [OK]

I am unable to boot to both normal and recovery modes.
I tried to run update and upgrade but the problem persisted.
i booted from live USB and ran the fix for packages and the fix for the boot file but the problem persisted.

I must add that i installed some packages using synaptic before i restarted my computer, packages that allows me to install .tar.gz files, but i don't know if it has anything to do with my situation.

Edit:
It turned out to be a lightdm issue, I fixed it by switching back to gdm, I hope this helps

I really appreciate your help.

---

