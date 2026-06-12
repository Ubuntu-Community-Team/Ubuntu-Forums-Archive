---
title: "Can't configure screen locking in Xubuntu"
date: 2011-05-15
forum: General Help
---

### Post by textist on 2011-05-15
Hello,

I'm having difficulty disabling the screen lock feature when resuming from suspend in Xubuntu 11.04 x64.  The screen lock seems to be implemented in xscreensaver, so I disabled the screen saver in the Settings Manager.  This did not work.  In the 'Power Manager' section of Settings Manager, I unchecked "lock screen when going for suspend/hibernate' and this did not work.  I found a possible workaround in a bug report that seems to describe the problem I'm having: [https://bugs.launchpad.net/ubuntu/+source/xubuntu-meta/+bug/159756](https://bugs.launchpad.net/ubuntu/+source/xubuntu-meta/+bug/159756) but the solution offered there (install gconf-editor and disable screen lock from there) did not work.  The bug report states that the problem was fixed in xfce4-utils 4.4.2-1ubuntu1, but from what I can tell the version of that package in 11.04 is newer than that.  The only thing that seems to work is to completely uninstall xscreensaver, but this seems like an awkward solution.  Any help would be greatly appreciated.  Thanks!

---

### Post by Toz on 2011-05-15
That bug report is from 2007.

Try this: In /etc/default/acpi-support, comment out the line```
LOCK_SCREEN=true
```

---

