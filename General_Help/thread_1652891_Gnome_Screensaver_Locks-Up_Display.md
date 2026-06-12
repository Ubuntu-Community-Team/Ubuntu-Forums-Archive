---
title: "Gnome Screensaver Locks-Up Display"
date: 2010-12-25
forum: General Help
---

### Post by JSeymour on 2010-12-25
Hi All,

Specifications:
    Dell PoweEdge 1600SC
    ATI Radeon HD 2400 Pro 256MB PCI graphics adaptor

    Ubuntu 9.10 "Karmic Koala"
    Linux 2.6.31-22-generic #69-Ubuntu SMP Wed Nov 24 08:51:08 UTC 2010 i686 
    ATI fglrx drivers
    Set up for dual-head display using two Princeton 19" monitors

    Using the Gnome desktop and screensaver

At some point, I suspect since the last kernel upgrade, I've begun experiencing a problem when the screen locks: I tap a key on the keyboard and the monitors wake up, but I get no "unlock" dialog.  I can *usually* Ctrl-Alt-F1, login and gracefully reboot the system, but sometimes I have to hit hard reset.

Any clues on what's causing this and how I can fix it?  For now I've disabled the screensaver in "System -> Preferences -> screensaver" (I *assume* that'll stop the problem), but that's not an optimal solution.

Thanks,
Jim

---

### Post by JSeymour on 2010-12-28
Nobody has any clues or suggestions?

Thanks,
Jim

---

### Post by noah++ on 2010-12-28
Have you perused any of the logs from the time of the lockups -- Xorg.log, syslog, etc?

---

### Post by karthick87 on 2010-12-28
Have you checked the option "Lock screen when screensaver is active" in your screensaver preferences??

---

### Post by JSeymour on 2010-12-30
> **noah++ said:**
> Have you perused any of the logs from the time of the lockups -- Xorg.log, syslog, etc?Thanks for the follow-up, Noah.

Only thing I've found of interest is
```

gdm-simple-slave[29823]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory

```in /var/log/syslog, prior to the reboot.  I've located that elsewhere in the logs, incl. areas that don't seem to have resulted in me rebooting.  There is an Xorg.log.0.old with a timestamp that matches the hour:minute of the syslog entry with the "custom.com" error message timestamp.  There's a lot of informational stuff in there.  Can't tell what's important and what's not.

I searched on the warning message.  Inconclusive results, incl. the instance by developers that the message has no bearing on anything.  Problems that *seem* related/associated with this continue to be reported by Ubuntu 10.x users.

The problem has not recurred since I disabled the screen saver/locker.

> **karthick87 said:**
> Have you checked the option "Lock screen when  screensaver is active" in your screensaver preferences??I think you misread my issue.  The problem isn't that screen-locking isn't happening, it's that, sometimes, when it does, I cannot make it **un-**happen.


Thanks,
Jim

---

### Post by spantch101 on 2011-01-05
check your power management utilities...(open synaptic and search pm-utils) if you are using a laptop with 1.4 installed remove and reinstall 1.3 [http://packages.ubuntu.com/de/lucid/all/pm-utils/download](http://packages.ubuntu.com/de/lucid/all/pm-utils/download) after installing 1.3 reboot ... fixes alot of power management issues in 10.10...

---

### Post by JSeymour on 2011-01-09
Thanks for the follow-up and suggestions, spantch101, but I'm not using a laptop.

Jim

---

### Post by TTGRULES on 2011-01-20
I am having the same issue? has anyone found a resolution? my screen does fine unless I Leave it locked overnight, or for a long period of time. Ive been restarting my computer every day for the past week. !!!!!

---

### Post by JSeymour on 2011-02-27
Closure, of a sort, to this?  After the next kernel update, and there have been one or two more, since then, the problems mysteriously went away.

Jim

---

### Post by patrick_the_fat on 2011-02-27
Save the headache, and disable it completely with these commands!  Ubuntu does not always listen when you tell it to disable the screensaver and power management.  You can add this script to your home folder, mark it as executable, and link to it using System > Preferences > Startup Manager:


#!/bin/bash

xset -dpms
xset s off
xset s noblank

Your screensaver will never disrupt you again.  Not a fix, but an easy solution!!

---

