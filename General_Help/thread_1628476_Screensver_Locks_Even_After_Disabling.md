---
title: "Screensver Locks Even After Disabling"
date: 2010-11-22
forum: General Help
---

### Post by wbar2 on 2010-11-22
I have disabled the screensaver from locking the computer and asking for a password. I did this by unchecking the box in System > Preferences > Screensaver which says 'Lock screen when screensaver is active.'

However, the screensaver still locks the screen. Any suggestions?

I'm running Ubuntu 10.10 64-bit on an HP Pavilion dv5.

---

### Post by wbar2 on 2010-11-23
I just realized that its not the screensaver. It has to do with after the computer comes back from being suspended to RAM. I don't see an option for disabling this under System > Preferences > Power Management. Does anyone know how to change this?

---

### Post by wbar2 on 2010-11-23
Found the solution here:
[http://ubuntuforums.org/showpost.php?p=9195930&postcount=9](http://ubuntuforums.org/showpost.php?p=9195930&postcount=9)

ALT+F2
Open gconf-editor.
Go to /apps/gnome-power-manager/lock/
Uncheck "Supsend"

---

