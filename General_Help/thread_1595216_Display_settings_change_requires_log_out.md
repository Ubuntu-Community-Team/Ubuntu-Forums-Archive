---
title: "Display settings change requires log out"
date: 2010-10-13
forum: General Help
---

### Post by steenbras on 2010-10-13
Have installed 10.10 on a Dell Studio XPS running AIT Radeon Mobility HD 3670.

Now if I connect up a second screen and choose gnome-display-properties, and modify the display resolution on the second screen (or deselect "Same image in all monitors", which appears enabled by default when I plug in a second screen), I get prompted to log out and log back in again.

Even if I choose to log out and back in again, the display configuration remains unchanged. It appears that only a full restart will do it.

With Lucid, changes were effected immediately, and did not require a logout, or restart.

This looks like a regression to me. Has anyone here managed to get a resolution?

---

### Post by Lefke123 on 2010-10-16
I have the exact same problem, but on a Toshiba P300 (also with an ATI Mobility Radeon 3650). I cannot even mirror the screens when I try at Monitors. Yet, when I'm at the login screen, both screens show exactly the same image...

On the other hand, via the ATI Catalyst Control Center, I can change whatever I want with the monitors. Logging in and out doesn't change anything, nor does restarting the computer.

So maybe try the Control Center for now? (Not really a fix, I know.)

UPDATE: I just removed the ATI drivers completely, and it fixed the problem for me.

---

### Post by steenbras on 2010-10-17
Bizarrely, after using the Catalyst Control Center and rebooting, the normal gnome-display-properties tool works normally. Not sure of whether I did anything other than that, but all seems ok now. Now all I need to do is get the touchpad to work after a resume and I'll be laughing.

---

