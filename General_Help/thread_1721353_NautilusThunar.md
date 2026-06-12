---
title: "Nautilus/Thunar?"
date: 2011-04-04
forum: General Help
---

### Post by galacticaboy on 2011-04-04
Is there a way I can remove Nautilus and replace it with Thunar. I like Thunar more and would like to use it.

---

### Post by wolfen69 on 2011-04-04
You don't need to remove nautilus to use thunar. Just create a launcher for thunar, and you're good to go.

---

### Post by 3Miro on 2011-04-04
If you like Thunar better, then just use it. If you want it associated with places and other applications, you will have to do this:

[https://help.ubuntu.com/community/DefaultFileManager](https://help.ubuntu.com/community/DefaultFileManager)

Needless to say, it is complicated and not recommended.

---

### Post by dzon65 on 2011-04-04
Try " gksu gedit /usr/share/applications/nautilus-folder-handler.desktop"
In the file, look for the line that reads *Exec=nautilus --no-desktop %U*. Change it so it reads *Exec=thunar %U*.  Save the file, log out and back in again.

---

### Post by galacticaboy on 2011-04-04
Okay then, that looks a bit to complicated. Thanks anyway though guys!

---

