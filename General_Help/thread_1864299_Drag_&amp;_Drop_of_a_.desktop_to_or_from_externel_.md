---
title: "Drag &amp; Drop of a .desktop to or from externel media is a move operation"
date: 2011-10-18
forum: General Help
---

### Post by mc4man on 2011-10-18
Just curious if anyone know why this is. It's the only file type I've ever seen that does this, all others are the expected copy
 
In other words - if I Drag a .desktop from a usb flash to my install it's moved from the flash drive
The same occurs if doing the opposite, if dragged from my ~/  to a flash drive it's also moved instead of copied
Has to be a real .desktop, not a file named .desktop, a minimal ex. - Type=Application seems to turn from copy to move

```
[Desktop Entry]
Version=1.0
Type=Application
Terminal=
Exec=
Name=
Icon=
```

---

### Post by crdlb on 2011-10-18
My guess is that they didn't want people to copy launchers thinking they were copying the actual application. It could just be a bug though. Nowadays, .desktop files usually remain in the applications folder to be referenced by name, so I can see how this behavior might not be noticed.

---

