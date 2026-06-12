---
title: "Truncate file/folder names?"
date: 2009-07-06
forum: General Help
---

### Post by trpnblies7 on 2009-07-06
Is there a way to have Ubuntu automatically truncate long file and folder names so that you only see the full name when you click on a file? For instance, if I had a folder named "Really Really Long Folder Name", it would show up as something like "Really Really L..." until I click on the icon. That way long names wouldn't throw off the layout of my folders.

---

### Post by CatKiller on 2009-07-06
It already does. You can modify the behaviour so that it truncates the filename after a different number of lines by opening **gconf-editor** and modifying the text_ellipsis_limit key in /apps/nautilus/icon_view, ../list_view and ../desktop, depending on which method you normally use to view files in Nautilus.

---

### Post by johnadverd on 2009-07-06
Hi, In the “after” scenario the program decides to *truncate* the *file name* and i can do nothing against it if i want to see the full *file name* and thing that But the most visible view is the desktop and this looked crappy in my eyes since I switched back from KDE to [I]Gnome.

[/I]

---

### Post by CatKiller on 2009-07-06
> **johnadverd said:**
> Hi, In the “after” scenario the program decides to *truncate* the *file name* and i can do nothing against it if i want to see the full *file name*

That's not true. You define the length of filename that you want to be displayed for each zoom level. If you want to see more detail, you just zoom in. It's not like it changes what the filename *is*, just how it's *displayed*.

---

### Post by trpnblies7 on 2009-07-06
Thanks! That worked great.

---

