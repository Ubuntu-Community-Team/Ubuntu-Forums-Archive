---
title: "&quot;Places&quot; menu doesen't work."
date: 2010-03-08
forum: General Help
---

### Post by the beekeeper on 2010-03-08
I was transferring files between computers, when the power was shut off.  After rebooting, all the items on the desktop are gone, and if you click on anything on the places menu, it pinwheels for about 20 seconds and then nothing happens.  I can load Firefox, and any of the programs installed, however.  Oddly enough, if I open office (or Mplayer) and try to open a file, I can see the entire contents of the home folder and open files.  How do I re-install the necessary components to make my places menu desktop work again?

---

### Post by cong06 on 2010-03-09
I have two ideas, one less destructive then the other.
1) try to do a disk check. If you open up the computer, when Grub is loading press "esc" and you get the boot menu. Choose "restore mode" and when the blue screen loads, go down to fsck.

2) If that fails to fix anything, then do the same procedure but this time go to "root" and run something like these:
Move the folder to another location
```

mv /home/<username> /home/<username>.backup

```
Make a new home directory folder and add correct permissions
```

mkdir /home/<username>
chown <username>:<username> /home/<username> 

```
(switching <username> for your username)
Basically just recreating your home directory. You'll loose all your settings, but you can still recover your documents from "/home/<username>.backup" and if you know how to you can restore specific settings from this same folder.

Good luck.

---

