---
title: "icon theme LXDE"
date: 2010-10-06
forum: General Help
---

### Post by ocurrente on 2010-10-06
Hi everyone, an Ubuntu newbie here!

I installed LXDE on Ubuntu 9.10, and only the first time i logged in, an error appears:

> GTK+ icon theme is not properly set

This usually means you don't have an XSETTINGS manager running. Desktop environment like GNOME or XFCE automatically execute their XSETTING managers like gnome-settings-daemon or xfce-mcs-manager.

If you don't use these desktop environments, you have two choices:
1. run an XSETTINGS manager, or
2. simply specify an icon theme in ~/.gtkrc-2.0.
For example to use the Tango icon theme add a line:
gtk-icon-theme-name="Tango" in your ~/.gtkrc-2.0. (create it if no such file)

NOTICE: The icon theme you choose should be compatible with GNOME, or the file icons cannot be displayed correctly. Due to the differences in icon naming of GNOME and KDE, KDE themes cannot be used. Currently there is no standard for this, but it will be solved by freedesktop.org in the future.but now I have lxde-settings-daemon running, however, i can only see the folders, but i can't see other file icons (mp3, jpg, rar, gif, etc.) and i can't open them directly.

I did what the error message say,  to create the gtkrc-2.0 file, but it didn't work.

I use lxappearance, this is the **config** file content in /home/user/.config/lxde
```
[GTK]
sNet/ThemeName=Loma
sNet/IconThemeName=Quickening
sGtk/FontName=Sans 10
iGtk/ToolbarStyle=3
```the file has exactly what i chose in lxappearance but the icons doesn't appear. I have to open them with right-click->open with... 

i found this, but i can't completely understand what it means or how to do it [http://wiki.archlinux.org/index.php/LXDE#Problems_when_updating_to_Version_0.4.1_of_lxsession.](http://wiki.archlinux.org/index.php/LXDE#Problems_when_updating_to_Version_0.4.1_of_lxsession.).

I've been looking for a couple of days, but i can't solve the problem.

well, I hope I've explained myself well, because i don't speak english properly.
I hope you can help me.

---

