---
title: "Xubuntu desktop icon text transparency"
date: 2011-10-21
forum: General Help
---

### Post by xubuhemmo on 2011-10-21
I change ubuntu to xubuntu and it's very good. Only few problems.
How I can get desktop icon text transparency.

---

### Post by Toz on 2011-10-21
Hello and welcome to the forums.

To get icon transparency on the desktop, create (or add to if it already exists) the file **~/.gtkrc-2.0** (a hidden file in your home directory), the following content:
```
style "xfdesktop-icon-view" {
    XfdesktopIconView::label-alpha = 0

    base[NORMAL] = "#000000"
    base[SELECTED] = "#000000"
    base[ACTIVE] = "#000000"

    fg[NORMAL] = "#ffffff"
    fg[SELECTED] = "#ffffff"
    fg[ACTIVE] = "#ffffff"
}
widget_class "*XfdesktopIconView*" style "xfdesktop-icon-view"

```

Either log out and back in again _or_ change the appearance theme to something else and back again for it to take effect.

---

### Post by scottbomb on 2011-11-06
Awesome! Thanks for this tip.

---

