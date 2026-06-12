---
title: "Backing up through live cd"
date: 2010-10-27
forum: General Help
---

### Post by Thatlinuxguy on 2010-10-27
I was updating my laptop from 10.04 to 10.10 and the fan stoped and the laptop overheated and shutdown in the middle of the update. So now I cannot use Ubuntu till I reinstall, but I was wondering if someone knew how to back up the homefolder through the live cd with permission to copy every file that is on their because the important files are the one I need permission for.

Please post up if you can help or have some idea:)

---

### Post by hhh on 2010-10-27
A little known fact... you can install Ubuntu, choose manual installation, point the install to the partition your old version is on and then choose NOT to format the partition and Ubuntu will install without touching your home folder.

Source (2nd paragraph)...
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

---

### Post by mikewhatever on 2010-10-28
Try launching the file browser with admin privileges, when in live session:

```
gksudo nautilus
```

---

