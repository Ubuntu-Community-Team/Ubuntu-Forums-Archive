---
title: "Filesystem Icon on Desktop?"
date: 2010-07-12
forum: General Help
---

### Post by Cam! on 2010-07-12
How would I go about putting a launcher on my desktop that opens my filesystem?

---

### Post by marshmallow1304 on 2010-07-12
Right-click on Desktop, "Create Launcher..."
Type: Location
Name: Filesystem (or whatever you want)
Location: /
Comment: Open the filesystem (or whatever you want)

You could also put
Location: computer:///
to open the same thing as Places->Computer


Then you can click on the launcher icon to select an appropriate icon (hint: there are lots of icons in /usr/share/icons/).

---

### Post by pastalavista on 2010-07-12
You can also just drag any entry in the places menu to the desktop.

---

### Post by ajgreeny on 2010-07-12
Use the configuration editor (Alt+F2 and type **gconf-editor**), then browse to apps-nautilus-desktop and you can set icons to show for several items on the desktop, eg, *Computer, Home, Trash, Network, *and*  Volumes visible*.

---

