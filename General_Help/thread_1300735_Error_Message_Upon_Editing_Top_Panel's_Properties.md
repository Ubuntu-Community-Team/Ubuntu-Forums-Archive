---
title: "Error Message Upon Editing Top Panel's Properties"
date: 2009-10-25
forum: General Help
---

### Post by Joseph Schwenker on 2009-10-25
I have been having a problem with the properties of my top panel.  Whenever I right click on it and click "Properties", the properties box comes up, but an error message that says:

```
The folder contents could not be displayed
Error stating file '/home/joseph/.themes/Mac4Lin_GTK_Aqua_v1.0/gtk-2.0/Panel': No such file or directory
```
every time I open the properties box.  I have long been rid of the Mac4Lin theme, but am still getting this error message.  How can I stop it from occurring again... and again... and again?  AHHHHHH!!!  Infinite loop!  Thanks!  I am using Ubuntu 9.04.

---

### Post by Joseph Schwenker on 2009-10-27
bump

---

### Post by Giblet5 on 2009-10-27
Log off.

Flip to the console via CtrlAltF1.

Log in.

```
mkdir .dotfiles
mv .gconf* .config .theme* .dotfiles
exit
```

Flip back to the GUI.

Log in.

You'll have to reconfigure everything (email, IM, etc), but that problem is solved.

---

