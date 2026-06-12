---
title: "Should this be filed as a bug?"
date: 2010-01-14
forum: General Help
---

### Post by Richard1979 on 2010-01-14
Or is it some intended feature?

Clicking on the desktop to ensure you are not using the shortcut in any application then using:

ALT + Sysrq + h (ALT + PrintSrcn + h)

Will immediately send the load through the roof and make the system unresponsive.
Mine reached a load average of 32 before I managed to click reboot.
After rebooting, fsck had to check/repair my home directory (ext3).

Running 9.10 x64, mostly a regular desktop install apart from /home and a few other mountpoints on different disks.

---

### Post by sanderd17 on 2010-01-14
Normally alt+sysrq keys are for killing apps and so.
Take a look here:
[http://www.junauza.com/2009/01/linux-keyboard-shortcuts-to-exit-safely.html]("http://www.junauza.com/2009/01/linux-keyboard-shortcuts-to-exit-safely.html")

---

### Post by bkratz on 2010-01-14
I would think that if a simple key combination can destroy your home directory, then it should be reported. ( I didn't have the guts to try it and see for myself!)

---

### Post by Richard1979 on 2010-01-14
> **sanderd17 said:**
> Normally alt+sysrq keys are for killing apps and so.
Take a look here:
[http://www.junauza.com/2009/01/linux-keyboard-shortcuts-to-exit-safely.html](http://www.junauza.com/2009/01/linux-keyboard-shortcuts-to-exit-safely.html)

That's kinda my point - ALT + Sysrq + h is supposed to be for the help files, not "go mental" :P

---

### Post by doas777 on 2010-01-14
I'm pretty sure that you on;y wanna use sysreq+h when in a VTTY, or other cli env.
it doesn't make sense that that description would hold for a gnome session.

---

