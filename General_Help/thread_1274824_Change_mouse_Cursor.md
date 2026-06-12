---
title: "Change mouse Cursor?"
date: 2009-09-25
forum: General Help
---

### Post by MegaLoler on 2009-09-25
I want to change the mouse cursor.  There is no Cursor tab in the mouse preferences, and when I launch Gcursor from the terminal, clicking on a new cursor or changing thr size doesn't work.  I'm using a g4 mac, that doesn't have anything to do with it, does it?  Thanks for any help.

---

### Post by ~sHyLoCk~ on 2009-09-25
Extracted it to /usr/share/icons ? 
Then:
```
sudo mkdir -p /usr/share/icons/default
cd /usr/share/icons/default && sudo gedit index.theme
```
Type:
```
[Icon-Theme]
Inherits = iconname
```

Save and exit. Reboot.

---

### Post by MegaLoler on 2009-10-26
I found that you can change the cursor from the Theme Customize button in the appearence preferences.  You click customize theme and the last panel is Cursor, for anyone else with this problem.

---

