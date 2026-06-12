---
title: "Command line top of screen"
date: 2009-10-11
forum: General Help
---

### Post by stanley82 on 2009-10-11
This has changed and I now have going left to right on top of screen.
Firefox, email, help followed by the an icon followed by Applications, places, System and the stuff on the right seems to be unchanged.  What do I do to restore this.  It happened before and it was suggested I delete a few files.  That fixed it but I lost my email settings.  I'm using Jaunty on a PC amd64 with Ubuntu straight.

     Any suggestions greatly appreciated.  Ian.

---

### Post by bryncoles on 2009-10-11
Your problem seems a little ambiguous. What are you trying to describe, and can you provide a screeny?

---

### Post by sisco311 on 2009-10-11
If you want to restore the default panels, then open a terminal and run:
```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```

If the panel dose not restart, press Alt+F2 and run:
```
gnome-panel
```

---

### Post by stanley82 on 2009-10-11
Great, that's fixed it for me.  Manny thanks Ian.

---

