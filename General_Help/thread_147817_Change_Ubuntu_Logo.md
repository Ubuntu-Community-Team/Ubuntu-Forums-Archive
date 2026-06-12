---
title: "Change Ubuntu Logo"
date: 2006-03-20
forum: General Help
---

### Post by Stambo00 on 2006-03-20
Ive been following several tutorials but I simply cannot change the logo beside Applications in the gnome menu. Could someone please direct me where the file is so I can change it to the gnome foot? Thanking you all in advance. :)

---

### Post by jrib on 2006-03-20
just backup  /usr/share/icons/hicolor/48x48/apps/distributor-logo.png and place another filel in its place.  For the gnome foot all you have to do is open applications > accessories > terminal:

```
 sudo mv /usr/share/icons/hicolor/48x48/apps/distributor-logo.png /usr/share/icons/hicolor/48x48/apps/distributor-logo.png_backup
``` (one line)

```
killall gnome-panel
``` (restarts your panel)

---

### Post by Stambo00 on 2006-03-20
Yes, Ive done that, but nothing changes (even after killall gnome-panel) Is it possible it could be residing somewhere else?

---

### Post by mr.p on 2006-03-20
[QUOTE=Stambo00]Yes, Ive done that, but nothing changes (even after killall gnome-panel) Is it possible it could be residing somewhere else?[/QUOTE]
Are you using the default icon set? Or a custom icon set?

---

### Post by Stambo00 on 2006-03-21
I changed the default icon set to one called "still life" What should I do? I changed the set back to "human" but I still had the same problem!

---

### Post by Stambo00 on 2006-03-22
*bump*

---

