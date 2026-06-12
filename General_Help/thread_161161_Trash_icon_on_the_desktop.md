---
title: "Trash icon on the desktop"
date: 2006-04-16
forum: General Help
---

### Post by xXx 0wn3d xXx on 2006-04-16
lol, I know this is a stupid question, but is there a way to get the trash icon on the desktop like dapper ? :???:

---

### Post by xenmax on 2006-04-16
System Tools -> Configuration Editor -> apps/nautilus/desktop - check the trash icon visible box.

---

### Post by ubernoob on 2006-04-16
It's not a stupid question. I was sure it was imposible since it is an applet and not an icon. But i found out that you can do:
gconf-editor
/apps/nautilus/desktop/trash_icon_visible

---

### Post by xXx 0wn3d xXx on 2006-04-16
[QUOTE=xenmax]System Tools -> Configuration Editor -> apps/nautilus/desktop - check the trash icon visible box.[/QUOTE]
Thank you, I seem to have tried everything but that :)

---

