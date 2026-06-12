---
title: "GTK+ toolbars height"
date: 2010-03-20
forum: General Help
---

### Post by toMeloos on 2010-03-20
Hi, I'm trying to reduce the size of the GTK+ toolbars maximize my screen use on a netbook. So far I've managed to reduce the size of the icons in the toolbar using the following settings in ~/.gtkrc-2.0

```
gtk-icon-sizes = "panel-menu=16,16:panel=16,16:gtk-menu=14,14:gtk-large-toolbar=14,14:gtk-small-toolbar=14,14:gtk-button=14,14:gtk-dnd=14,14:gtk-dialog=14,14"
gtk-toolbar-icon-size = GTK_ICON_SIZE_SMALL_TOOLBAR
gtk-toolbar-style = GTK_TOOLBAR_ICONS
```

The problem is that this does not reduce the height of the toolbar itself, just the icons in it. It just leaves more blank space in the toolbar below the icons. How can I make it smaller?

p.s. to prevent confusion: I'm focusing on the toolbars inside applications, not the general gnome-panel!

---

