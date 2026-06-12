---
title: "Odd Kernel issue"
date: 2009-09-12
forum: General Help
---

### Post by ppirilla on 2009-09-12
I rebooted my computer to deal with some cabling issues.  It seemed to boot with no issue, but the machine just sat there after I entered my password.  It didn't freeze -- I still had control of the mouse, and was able to tell the machine to restart, but it would not log in.

After some fiddling, I tried booting under Kernel Image 2.6.28-14 instead of 2.6.28-15, and things seem to be working fine.

So, a) Anyone have any idea why the newer kernel is breaking things?  b) If not, what do I do to force grub to automatically boot the older kernel?  I would just uninstall, but the next time i update through apt-get, i think it will come right back.

---

### Post by akakingess on 2009-09-12
You could install startupmanager and set the older kernel as the default.
```
sudo apt-get install startupmanager
```

---

