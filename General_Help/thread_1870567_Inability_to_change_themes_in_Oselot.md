---
title: "Inability to change themes in Oselot?"
date: 2011-10-27
forum: General Help
---

### Post by sports fan Matt on 2011-10-27
Even moving the theme to usr/share/themes, "A new Hope" gtk can't be chosen from the drop down menu.  I assume this is by design?  Anyone know?

Matt

---

### Post by mcduck on 2011-10-27
Is it a GTK3 theme? If it's only GTK2, it's not going to work in 11.10.

The theme dialog only shows GTK3 themes, although you'll actually want the theme you use to include both GTK3 and GTK2 support for compatibility with older applications that might still be using GTK2.

---

### Post by sports fan Matt on 2011-10-27
Not sure, but I just downloaded elegant brit gtk 3 and no choice there either, do I need to log out/back in?

---

### Post by mcduck on 2011-10-27
Are you using the [Gnome-tweak-tool]("apt:gnome-tweak-tool") to change the themes? It should recognize it immediately without having to log out.

I suppose I should also have mentioned that the Appearance dialog will only list the couple of complete themes configured, if you want to select GTK, icon and window border themes separately you need to use the gnome-tweak-tool.

---

