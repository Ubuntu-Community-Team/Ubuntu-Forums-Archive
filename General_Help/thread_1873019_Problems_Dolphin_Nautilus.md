---
title: "Problems Dolphin Nautilus"
date: 2011-10-31
forum: General Help
---

### Post by cscj01 on 2011-10-31
I recently upgraded to Oneiric x86_64 from Natty x86_64, and I am using Gnome Classic (without effects).  Now Dolphin seems to be my default file browser, at least from the Places menu.  If I choose any option from Places, I get Dolphin.  I can choose disk drives from my desktop and get Nautilus.  I can get Nautilus from a terminal session.  I checked desktop>gnome>applications>component_viewer with gconf-editor and it shows > exec nautilus %s  I believe this is where I set my default file browser.  I do not want Dolphin.  Rather, I want Nautilus.  What is going on here?

---

### Post by collisionystm on 2011-10-31
Go to system settings

System

Default applications

Change file manager to nautilus

---

### Post by cscj01 on 2011-11-01
There is no File Manager choice under Default Applications.  I am using Gnome Classic, so it must have been removed.

---

### Post by Mark Phelps on 2011-11-01
If you want a multi-panel file manager, look into Gnome Commander.

---

### Post by cscj01 on 2011-11-01
While I appreciate the suggestions to switch to another file manager, I really would like to resolve my issue.  Perhaps it's a bug, but I thought someone may have encountered this issue or might have some idea as to why it was occurring.
> **Mark Phelps said:**
> If you want a multi-panel file manager, look into Gnome Commander.I do have Gnome Commander installed, but I also like Nautilus.  I use Gnome Commander for renaming a group of files, for which I find it really helpful.  There may be other reasons for using Gnome Commander, but I haven't had the need to discover those reasons. Other than that, I use Nautilus.

---

### Post by cscj01 on 2011-11-02
I solved this problem by doing the following:```
gedit  ~/.local/share/applications/mimeapps.list 
```
added this line```
mnode/directory=nautilus-home.desktop
```Now if I open a file browser by going to the Places menu, Nautilus is used.  Thanks go to Colin Keenan who posted in> Oneiric Known Issues threadSo I'm happy and will marked this thread solved.  I don't know why that fixed it, but it did.

---

