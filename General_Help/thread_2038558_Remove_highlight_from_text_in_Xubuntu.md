---
title: "Remove highlight from text in Xubuntu?"
date: 2012-08-06
forum: General Help
---

### Post by Uncle Spellbinder on 2012-08-06
Hi, all.

Is there a way to remove highlited text from desktop icons in Xubuntu?

[IMG]http://i48.tinypic.com/14bhv0m.jpg[/IMG]


I'm liking the XFCE desktop, but the highlighted text is highly annoying. Seems white lettering and no highlight would make more sense.

Any help appreciated.

---

### Post by Toz on 2012-08-06
Create a file called ~/.gtkrc-2.0 in your home directory with the following content:
```
######################################################################################
#desktop icon transparency tweak
style "xfdesktop-icon-view" {
    XfdesktopIconView::label-alpha = 0

    base[NORMAL] = "#000000"
    base[SELECTED] = "#000000"
    base[ACTIVE] = "#000000"

    fg[NORMAL] = "#ffffff"
    fg[SELECTED] = "#ffffff"
    fg[ACTIVE] = "#ffffff"

    XfdesktopIconVIew::cell-spacing = 0
    XfdesktopIconView::cell-padding = 0
    XfdesktopIconView::cell-text-width-proportion = 2.0

}
widget_class "*XfdesktopIconView*" style "xfdesktop-icon-view"
```

Change the appearance theme away from and back to your theme to have the change take effect.

---

### Post by Uncle Spellbinder on 2012-08-07
Thanks, Toz. I suppose I need to open leafpad and paste the text you provided and save it in home as *.gtkrc* ?

In any event, I'll be installing Xubuntu as dual-boot with Windows 7 on my laptop. Once installed and updated, I'll give it a shot.

---

### Post by Toz on 2012-08-07
Sorry, the file should  be called **.gtkrc-2.0** (I'll edit my original post and make the correction). Just make sure the file is saved in your home directory.

---

### Post by Uncle Spellbinder on 2012-08-07
Will do. Thanks, Toz. Once installed, I report back in this thread.

Thanks again for the assistance!

---

