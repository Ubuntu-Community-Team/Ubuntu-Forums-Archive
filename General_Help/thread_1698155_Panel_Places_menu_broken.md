---
title: "Panel Places menu broken"
date: 2011-03-01
forum: General Help
---

### Post by gseward on 2011-03-01
In my Places menu, in the panel, any location I pick takes me to "Appearance Preferences/Background", ANY place; Home, Documents, Download, Pictures, etc...
If I go to Nautilus Places, everything works fine, as do all the Nautilus Bookmarks. I tried removing the menu from the panel and adding it back, no change, problem still there.
Any ideas?
Sorry about posting this twice, but I didn't want it in a (SOLVED) thread, and couldn't figure out how to delete it.
Gil

---

### Post by Krytarik on 2011-03-02
Open the file "~/.local/share/applications/mimeapps.list" and lookup the entry for "inode/directory", it should be like this:
```
inode/directory=nautilus-folder-handler.desktop;
```
Here is a good explanation of what may have caused it:
[http://ubuntuforums.org/showthread.php?t=1675491](http://ubuntuforums.org/showthread.php?t=1675491)

---

### Post by bebopiiam on 2011-03-16
> **Krytarik said:**
> Open the file "~/.local/share/applications/mimeapps.list" and lookup the entry for "inode/directory"....
Hi.  I installed VLC and it created this problem too.  I've forgotten if I used Synaptic or the Ubuntu Software Center but something modified the mimeapps.list to look like:
[Added Associations]
inode/directory=vlc.desktop;totem.desktop;

Your fix got things working again.  I'll cross post to the link you gave to let them know about this.

Thanks!

---

