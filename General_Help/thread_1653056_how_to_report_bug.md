---
title: "how to report bug"
date: 2010-12-26
forum: General Help
---

### Post by mahmoodn on 2010-12-26
I want to report a bug to launchpad, but it seems that launchpad only accepts through apport-bug. I don't want to do that since when I run apport-bug, it doesn't do any thing and stuck at "collecting information". Is there any way like bugs.kde.org to report bugs?

---

### Post by mikewhatever on 2010-12-26
May I ask what the bug is? What package is it against?

---

### Post by mahmoodn on 2010-12-26
There is a problem with nouveau driver that causes unwanted random logout. I see this in system.log:
```
010-12-21 11:13:40	localhost	kernel	[ 6659.196585] [drm] nouveau 0000:01:00.0: nouveau_channel_free: freeing fifo 2
2010-12-21 11:13:40	localhost	kdm[845]	X server for display :0 terminated unexpectedly
2
```

---

### Post by mikewhatever on 2010-12-26
So, just to make sure, if 'apport-bug nouveau' doesn't work for you, try the [Launchpad's bug form]("https://bugs.launchpad.net/ubuntu/+filebug/?no-redirect").

---

### Post by karthick87 on 2010-12-26
[https://wiki.kubuntu.org/Kubuntu/Bugs/Reporting](https://wiki.kubuntu.org/Kubuntu/Bugs/Reporting)

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

[https://wiki.kubuntu.org/Apport](https://wiki.kubuntu.org/Apport)

---

