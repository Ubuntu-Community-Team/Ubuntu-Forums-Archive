---
title: "Mounted Hard Disk doesn't appear in Desktop"
date: 2009-11-23
forum: General Help
---

### Post by meson2439 on 2009-11-23
All my mounted drives doesn't appear on my Desktop. It is definitely mounted but simply not visible. I can still navigate to the location in the /media/... 

It is not a major problem but very inconvenient because I have to unmount them from the terminal each time. The problem started after I experimented with liveusb. At first, the problem only appears when I run liveusb but afterwards the behaviour persist even when liveusb are not running. Does anybody has an idea how to solve this?

Thanks in advance.

---

### Post by Andreas1 on 2009-11-23
run "gconf-editor" and see if /apps/nautilus/desktop/volumes_visible is checked.

---

### Post by meson2439 on 2009-11-23
That solved everything... thanks

---

### Post by j22 on 2010-01-01
I have the same problem but volumes_visible is checked in the config-editor.

Anyone have any suggestions?
Thanks.

---

