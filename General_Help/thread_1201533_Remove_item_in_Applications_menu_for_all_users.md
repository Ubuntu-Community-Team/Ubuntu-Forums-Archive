---
title: "Remove item in Applications menu for all users"
date: 2009-07-01
forum: General Help
---

### Post by XCan on 2009-07-01
Does anyone know how to remove an item from the Applications menu so that it doesn't show up for any users on the system, but be only accessible through the terminal?

---

### Post by sisco311 on 2009-07-01
rename the appropriate .desktop file in /usr/share/applications.

for example to hide *Hardware Drivers*:
```
sudo mv /usr/share/applications/jockey-gtk.desktop /usr/share/applications/jockey-gtk.desktop.hide
```

---

### Post by XCan on 2009-07-01
Thanks sisco311, it works perfectly!

---

