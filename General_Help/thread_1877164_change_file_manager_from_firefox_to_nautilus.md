---
title: "change file manager from firefox to nautilus?"
date: 2011-11-07
forum: General Help
---

### Post by plethodon on 2011-11-07
Ubunto 11.10: Can I change the file manager from firefox to nautilus?  thanks

---

### Post by plethodon on 2011-11-07
p.s., using Gnome Classic

---

### Post by Enigmapond on 2011-11-07
1st, Welcome to the forum.:D

2nd - Your question doesn't really make much sense. Firefox is an internet browser and Nautilus is the File Manager for you desktop environment. One has nothing to do with the other.

---

### Post by mc4man on 2011-11-07
I'd guess you did an update to 11.10 - 
see here for a command to fix or open link for how to fix thru a mimeapps.list edit 
(link also has link to bug on

[http://ubuntuforums.org/showthread.php?p=11431237#post11431237](http://ubuntuforums.org/showthread.php?p=11431237#post11431237)

---

### Post by plethodon on 2011-11-07
The drop down items in the Places menu, e.g., Home Folder, Desktop, etc., bring up firefox as a file manager. I can only launch nautilus by starting in a terminal. Can I change the drop down file manager to nautilus?

---

### Post by Enigmapond on 2011-11-07
Then as mc4man just posted. Open a terminal and do:

```
sudo ln -s /usr/share/applications/nautilus.desktop /usr/share/applications/nautilus-folder-handler.desktop

```

That will fix the bug.

---

### Post by plethodon on 2011-11-07
Changed mimeapps.list as in linked post and problem solved.

Thanks!

---

