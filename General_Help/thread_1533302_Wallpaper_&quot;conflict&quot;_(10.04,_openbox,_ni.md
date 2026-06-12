---
title: "Wallpaper &quot;conflict&quot; (10.04, openbox, nitrogen, pcmanfm)"
date: 2010-07-17
forum: General Help
---

### Post by El_Belgicano on 2010-07-17
Hi everyone, it's probably just a quite obvious detail i'm missing here, but i got some conflict between two wallpapers.

My ubuntu flavour:
- fresh install of 10.04
- strip away some bits (evolution, and other "junk" in my eyes...)
- install some useful apps: skype, thunderbird, among others...
- install nitrogen for wallpaper management
- install pcmanfm for file management (un-checking "manage wallpaper")

At startup:
- usual login/password (text-based)
- "startx" command
- openbox starts
*- nitrogen sets the wallpaper i want.*
then:
*- some other app sets the wallpaper back to the lucid lynx standard.*

The odd thing:
in $HOME/.cache/wallpaper/ , i found the same image i don't want, i removed the wallpaper folder and by the next reboot, there it was again...

Where ami missing something?

TIA,


EDIT: 
solved: ```
gconftool-2 --set /apps/gnome_settings_daemon/plugins/background/active --type bool False
```

---

