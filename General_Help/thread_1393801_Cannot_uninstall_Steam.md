---
title: "Cannot uninstall Steam"
date: 2010-01-29
forum: General Help
---

### Post by Cunnilingus on 2010-01-29
I am having a bit of a problem with Wine as I cannot remove any of the programs that I have installed in it, namely Steam. Even if I try to uninstall wine via "sudo apt-get remove wine" I can still navigate to Steam through Applications - Wine - Programs - Steam. I don't know what to do. I've even tried the "Uninstall Wine Software" option to get rid of Steam but that has also failed.

---

### Post by raktarok on 2010-01-29
You have used the wine uninstaller right? So all the program files are probably gone. To confirm that the files are all gone, check the folder .wine/drive_c/Program Files in your home folder. You will have to press Ctrl+h to see the .wine folder - it's hdden. Then see if there are any files related to steam, and if there are, delete them manually.

To remove the menu entry, navigate to .local/share/applications/wine/Programs/, again in your home folder. And delete the .desktop file related to steam. You may have to logout to see the changes.

---

### Post by Cunnilingus on 2010-01-29
Worked like a charm, thanks!

---

### Post by raktarok on 2010-01-29
Glad to hear that!

---

