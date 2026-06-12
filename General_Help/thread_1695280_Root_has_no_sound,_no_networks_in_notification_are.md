---
title: "Root has no sound, no networks in notification area"
date: 2011-02-25
forum: General Help
---

### Post by Rebelli0us on 2011-02-25
Is Root's profile broken? No sound, stuff missing from the notification tray... it happens in most installations. Any way to fix this?

---

### Post by Ocxic on 2011-02-25
Don't login as root, it's a security risk.

---

### Post by Rebelli0us on 2011-03-02
The sound system works fine, it even does the usual drum-roll at login screen, and all users have sound **except** Root! How do you fix this?

---

### Post by Krytarik on 2011-03-02
It is absolutely not necessary to actually and even graphically login as root!!
And, like *Ocxic*, it is also a security risk!

Instead use "sudo" and "gksudo" for administrative tasks, make sure to use "gksudo" for graphical apps:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

EDIT: You may find that there are some really rare occasions where you need to actually login as root (at the command line), but you really do not ever need to login graphically.

---

