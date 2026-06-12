---
title: "Urgent: aptitude failed mid-upgrade"
date: 2011-10-21
forum: General Help
---

### Post by Lyuokdea on 2011-10-21
Hi All, 

Was performing an upgrade from 10.10 to 11.04, halfway through it asked about upgrading some file i had user upgraded, and i decided to check the difference between the two configuration files. 

At that point, less (or whatever text file it had brought me into) failed, and now I can't get back to finish the installation. Loading another command prompt gives me:

**** VTE ***: Failed to load terminal capabilities from '/etc/termcap'

I can get in with terminal capabilities through ssh, but i can't find away to restart the upgrade. If i try to rerun:

sudo do-release-upgrade

```
Unable to get exclusive lock 

This usually means that another package management application (like 
apt-get or aptitude) already running. Please close that application 
first. 
=== Command detached from window (Fri Oct 21 12:49:19 2011) ===
=== Command terminated with exit status 1 (Fri Oct 21 12:49:19 2011) ===
```

Which makes me think aptitude is still running somewhere, but I have no control over it, how do I get that back?

~Lyuokdea

---

### Post by Lyuokdea on 2011-10-21
I don't see any PID corresponding to something like aptitude or apt-get when i run ps -A | less

Thanks,

~Lyuokdea

---

