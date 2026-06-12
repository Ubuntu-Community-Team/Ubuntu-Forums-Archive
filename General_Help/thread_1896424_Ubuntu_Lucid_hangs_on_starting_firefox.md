---
title: "Ubuntu Lucid hangs on starting firefox"
date: 2011-12-16
forum: General Help
---

### Post by kesavachandran on 2011-12-16
My Lucid 2.6.32.36 generic upgraded from the basic mode has performed very well since inception months ago.Recently the system hangs on starting Firefox.I installed Firefox debug via Synaptic but the relief was short lived.Tried to use the command line without benefit.The mouse pointer freezes on the desktop.System has to be rebooted to access Firefox.In the Hanged state ALT+CTRL+DEL will not shut down system,have to switch it off.Shall appreciate suggestions ,help

---

### Post by hansdown on 2011-12-16
Hi, kesavachandran.

This "should" help.

Thanks to, ubuntu geek.

[http://www.ubuntugeek.com/how-to-fix-firefox-slow-problem-in-ubuntu-10-04lucid.html](http://www.ubuntugeek.com/how-to-fix-firefox-slow-problem-in-ubuntu-10-04lucid.html)

---

### Post by lovinglinux on 2011-12-16
Please start Firefox in safe mode and test it, then start a clean profile and report the results.

Safe Mode:

```
firefox -safe-mode
```

New Profile:

```
firefox -P
```

---

### Post by kesavachandran on 2011-12-17
Thanks to hansdown and lovinglinux for the prompt response.While seeking help , suspected a Virus as the cause and installed CLAMAV,kept action on your remedies pending.CLAMAV seems to have restored Firefox to normalcy.It proves that Firefox too has gained wider attention of Virus Mongers and anti virus is now a must on Linux distros.Have saved remedies suggested by hansdown and lovinglinux for a rainyday:D

---

### Post by hansdown on 2011-12-17
Glad you fixed it, kesavachandran.

---

