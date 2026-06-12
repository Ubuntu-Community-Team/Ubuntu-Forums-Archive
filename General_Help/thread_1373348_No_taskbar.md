---
title: "No taskbar"
date: 2010-01-05
forum: General Help
---

### Post by unclesamslair on 2010-01-05
starting up xubuntu 9.10 on my dual booted inspiron 1501 (vista) and the desktop pops up, but there's no taskbar or anything just the desktop.

All this after fixing my grub 
([http://ubuntuforums.org/showpost.php?p=8614400&postcount=26](http://ubuntuforums.org/showpost.php?p=8614400&postcount=26))
([http://ubuntuforums.org/showthread.php?t=1326788&page=3](http://ubuntuforums.org/showthread.php?t=1326788&page=3))
([http://ubuntuforums.org/showthread.php?t=1326788&page=4](http://ubuntuforums.org/showthread.php?t=1326788&page=4))

I popped up a terminal and installed tree to show me the filesystem. All my files are still there I then ran synaptic and tried to see if any packages were missing but I don't know much so now I'm stuck with another problem.

help is very much appreciated.

---

### Post by Leppie on 2010-01-05
right click on your desktop, go to Applications>Settings>Panel, see if a panel should be active. Check that the panel does not have the "Autohide" option checked (bottom right of the dialogue) nor 100% transparancy.

---

### Post by unclesamslair on 2010-01-05
> **Leppie said:**
> right click on your desktop, go to Applications>Settings>Panel, see if a panel should be active. Check that the panel does not have the "Autohide" option checked (bottom right of the dialogue) nor 100% transparancy.

Applications>Settings>Panel does absolutely nothing.

---

### Post by Leppie on 2010-01-05
if you still have the terminal open, try adding another user:
```
$sudo adduser test
```

log out as the current user and log in as the newly created test user, see if this user has the same issue as you have.
there may also be errors on your installation media, did you check the cd on errors?

---

### Post by unclesamslair on 2010-01-05
> **Leppie said:**
> if you still have the terminal open, try adding another user:
```
$sudo adduser test
```

log out as the current user and log in as the newly created test user, see if this user has the same issue as you have.
there may also be errors on your installation media, did you check the cd on errors?

taskbars and everything else work on test user account. cd used to install xubuntu didn't have any defects before i installed xubuntu and it still doesn't but since then i have reduced the size of my windows partition to make free space for a test install of mythbuntu and then i erased the mythbuntu partition and then rebooted when my comp started it showed me the grub rescue prompt. I fixed it on this forum ([http://ubuntuforums.org/showthread.php?t=1326788&page=4](http://ubuntuforums.org/showthread.php?t=1326788&page=4)) and now I have this problem :confused:

---

### Post by Leppie on 2010-01-05
try renaming your profile's config folder:
```
mv ~/.conf ~/.config.old
```

log out and log in again.

---

### Post by unclesamslair on 2010-01-07
this worked out for me perfectly

Alt+F2 and type xfce-panel

---

