---
title: "Gimp closes when i click on toolbox??"
date: 2010-07-06
forum: General Help
---

### Post by rahilm on 2010-07-06
I have gimp v2.6.8 installed via the repositories. I decided to crop an image and so opened it in gimp. but when i click on the icon , gimp closes. I fired it up again to check it. It closed even when i clicked the icon with a blank file. Further testing revealed that gimp will close when clicked on crop. and basically any icon on the toolbox.
it happens randomly, sometimes a click on rectangle select will close it. sometimes it won't..

Here's the error if anybody wants it.
```

rahil@rahil-desktop:~$ gimp
/home/rahil/.themes/Finery/gtk-2.0/gtkrc:256: Unable to locate image file in pixmap_path: "panel_bg.png"
gimp: fatal error: Failed to register GObject with DBusConnection

(script-fu:3277): LibGimpBase-WARNING **: script-fu: gimp_wire_read(): error


```

---

### Post by greyfox1 on 2010-07-06
Looks like you're having the same issue described [here]("https://bugs.launchpad.net/ubuntu/+source/appmenu-gtk/+bug/598321"). You might want to try removing the appmenu-gtk package as is recommended in the LP thread.

---

### Post by rahilm on 2010-07-07
Works..

---

