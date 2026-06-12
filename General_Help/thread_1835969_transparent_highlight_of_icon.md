---
title: "transparent highlight of icon"
date: 2011-08-30
forum: General Help
---

### Post by tweaku on 2011-08-30
I want to do more transparent highlight of icon when I select the icon on desktop. My code of ~/.gtkrc-2.0 is:
```
style "xfdesktop-icon-view" {
    XfdesktopIconView::label-alpha = 75

    base[NORMAL] = "#000000"
    base[ACTIVE] = "#000000"
base[SELECTED] = "#000000" # I want to do this element more transparent.

    fg[NORMAL] = "#ffffff"
    fg[SELECTED] = "#ffffff"
    fg[ACTIVE] = "#ffffff"
}
widget_class "*XfdesktopIconView*" style "xfdesktop-icon-view"
```
How I can do this?

---

### Post by tweaku on 2011-09-02
the command to do selected base more transparent:
```
XfdesktopIconView::selected-label-alpha = 140
```

---

