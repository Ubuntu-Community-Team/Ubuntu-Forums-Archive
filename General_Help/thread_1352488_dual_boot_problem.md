---
title: "dual boot problem"
date: 2009-12-11
forum: General Help
---

### Post by romanskier on 2009-12-11
I'm using a dual boot with windows 2000 and Ubuntu. Initially worked well, but now on the grub page I can not select windows. No keystrokes are recognised and Ubuntu boots. How can I get to Windows?

---

### Post by joes7 on 2009-12-11
Try to update / reinstall GRUB.

---

### Post by romanskier on 2009-12-11
Thanks joes 7. How does one update/reinstall grub?

---

### Post by oldfred on 2009-12-12
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Just make sure you follow the directions for the version of grub. If you mix instruction it can make for a real mess. If you have Karmic as a new install you have grub2. Otherwise you should have grub legacy (.97) unless you manually updated to grub2. If you have menu.lst then it is old grub.

---

