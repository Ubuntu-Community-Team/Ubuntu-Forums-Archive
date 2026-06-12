---
title: "HDD partition full, system crashed, cannot access files"
date: 2010-07-12
forum: General Help
---

### Post by seoras on 2010-07-12
I have been caught out by the failure of Ubuntu to report when running out of disk space.

Today Thunderbird crashed, then Ubuntu crashed and on rebooting flashed a message that disk space was low and click OK to empty Trash, I clicked OK but now I cannot access the system, I get an error message that the configuration defaults for gnome power manager have not been installed correctly.

I removed and reinstalled gnome-power-manager in terminal mode - no effect.
I then booted with live CD and discovered that the 180Gb partition Ubuntu is on is full. However with Live CD and GParted I have created 11Gb of free space but I cannot resize the Ubuntu partition.

With Live CD, when I mount the Ubuntu partition and navigate to /home/myName it says there are no files??? which means I cannot see if Trash has been emptied.

With Live CD Terminal I have tried rm -rf ~/.Trash/* with apparently no effect.

My last resort will be to removed the HDD from the PC and tray to copy data onto an new bigger disk. But if anyone has any other ideas I'd be grateful for suggestions.

Cheers
Seoras

---

### Post by MooPi on 2010-07-12
I would try sudo command when trying to access either the trash bin or rm files. Just a hunch. Maybe try this as well > gksu nautilus when navigating with live CD.

---

### Post by seoras on 2010-07-12
Yeh, I tried that but no luck. 

I may have solved the problem though, I'm working on it now and will post back if successful.

Cheers

---

