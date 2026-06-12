---
title: "how to anti alias fonts in gnome 3?"
date: 2012-03-20
forum: General Help
---

### Post by lightsaberlesbian on 2012-03-20
I can't seem to set this feature back.

---

### Post by TeoBigusGeekus on 2012-03-20
Do you have a settings.ini for gtk3?
If not create one at ~/.config/gtk-3.0 and put this line in it
```
gtk-xft-antialias = 1
```
My whole settings.ini file
```
[Settings]
gtk-theme-name = GnomishDark
gtk-icon-theme-name = Token-Light
gtk-font-name = Droidsans 10
gtk-cursor-theme-name = FlatbedCursors-LH.Black.Regular
gtk-cursor-theme-size = 0
gtk-toolbar-style = GTK_TOOLBAR_ICONS
gtk-toolbar-icon-size = GTK_ICON_SIZE_SMALL_TOOLBAR
gtk-button-images = 0
gtk-menu-images = 0
gtk-enable-event-sounds = 1
gtk-enable-input-feedback-sounds = 1
gtk-xft-antialias = 1
gtk-xft-hinting = 1
gtk-xft-hintstyle = hintslight
gtk-xft-rgba = rgb
```

---

### Post by princeofnam on 2012-03-21
I don't even have a GTK 3.0 folder. is that normal? I could have sworn also that I changed this function via gnome Tweak but for whatever reason it won't revert to normal again

---

### Post by mraandtux on 2012-03-21
> **princeofnam said:**
> I don't even have a GTK 3.0 folder. is that normal? I could have sworn also that I changed this function via gnome Tweak but for whatever reason it won't revert to normal again
See this post:
[http://ubuntuforums.org/showthread.php?p=11322965](http://ubuntuforums.org/showthread.php?p=11322965)

---

