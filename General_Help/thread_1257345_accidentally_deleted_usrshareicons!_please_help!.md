---
title: "accidentally deleted /usr/share/icons! please help!"
date: 2009-09-03
forum: General Help
---

### Post by mephist0pheles on 2009-09-03
i accidentally deleted /usr/share/icons while trying to delete a specific part of the icons folder...and, predictably, all my icons are now gone:(

how can i get them back? please help!

---

### Post by mephist0pheles on 2009-09-03
i think i also deleted some...linux generic headers or something...and some python package that sounded important...is that bad?

---

### Post by sisco311 on 2009-09-03
> **mephist0pheles said:**
> i accidentally deleted /usr/share/icons while trying to delete a specific part of the icons folder...and, predictably, all my icons are now gone:(

how can i get them back? please help!

reinstall gnome-icon-theme, human-icon-theme and tangerine-icon-theme:
```
sudo apt-get install --reinstall gnome-icon-theme human-icon-theme tangerine-icon-theme
```

> **mephist0pheles said:**
> i think i also deleted some...linux generic headers or something...and some python package that sounded important...is that bad?

yep, it's bad. how did you delete the files/folders?

---

### Post by mephist0pheles on 2009-09-03
[http://ubuntuforums.org/showthread.php?t=845210](http://ubuntuforums.org/showthread.php?t=845210)
i went to this thread for help...didn't help...instead, when i tried one of the command lines, it deleted those headers files or whatever they are...how can i fix the headers and stuff?

---

### Post by mephist0pheles on 2009-09-03
so i tried that reinstall line u gave me...didn't do anything...?

EDIT: nvm, it worked. thanks :)

---

### Post by mephist0pheles on 2009-09-03
i think it was the very last line of code of that thread that i tried that had me delete those linux generic headers and whatnot...or possibly the one b4 it...how can i undo it?

EDIT:```
dpkg -S /usr/share/icons | cut -d: -fl | sed 's/,//g; | xargs sudo aptitude reinstall
```i think thats what deleted those important-sounding files/folders

---

### Post by mephist0pheles on 2009-09-03
more importantly, why is my pointer still black? it becomes a watch whenever something is loading instead of the standard ubuntu loading icon. 
and my mines icon is gone along with my drawer icon and my fore quit icon...

---

### Post by mephist0pheles on 2009-09-03
```
(totem:3324): Gtk-WARNING **: Could not find the icon 'lpi-help'. The 'hicolor' theme
was not found either, perhaps you need to install it.
You can get a copy from:
    http://icon-theme.freedesktop.org/releases

** (totem:3324): CRITICAL **: failed to load icon 'lpi-help': Icon 'lpi-help' not present in theme

(totem:3324): Gtk-CRITICAL **: gtk_icon_theme_load_icon: assertion `error == NULL || *error == NULL' failed

** (totem:3324): CRITICAL **: failed to load icon 'lpi-translate': Icon 'lpi-help' not present in theme

(totem:3324): Gtk-CRITICAL **: gtk_icon_theme_load_icon: assertion `error == NULL || *error == NULL' failed

** (totem:3324): CRITICAL **: failed to load icon 'lpi-bug': Icon 'lpi-help' not present in theme

```

when i run totem i get this:confused:

---

