---
title: "Backing Up Menus and Preferences"
date: 2009-06-26
forum: General Help
---

### Post by measekite on 2009-06-26
I spent much time creating a custom menu system and custom panels.  I would like to know how to back them up and restore them in Jaunty?

There were commands in Feisty but when push came to shove it did not work as advertised.

---

### Post by jerrrys on 2009-06-27
maybe all you need is a simple backup

[http://www.ubuntugeek.com/backup-and-restore-your-ubuntu-system-using-sbackup.html](http://www.ubuntugeek.com/backup-and-restore-your-ubuntu-system-using-sbackup.html)

---

### Post by drs305 on 2009-06-27
You can save and restore your panels with the following commands:
To save: 	```
gconftool-2 --dump /apps/panel > **~/Desktop/panels**
```
To restore: 	```
gconftool-2 --load **~/Desktop/panels** && killall gnome-panel
```

They won't transfer completely to another machine because they are referenced by applet numbers specific to the machine they were created on. The save command will recreate the panel on the existing machine if it's lost. The settings are also stored in $HOME/.gconf/apps/panel if you prefer to back up the folder itself.

**[COLOR="DarkRed"]ADDED:[/COLOR]**
As far as menus, your menus are somewhat controlled by files in /etc/xdg/menus/ (*applications.menu & settings.menu*)  and are stored in $HOME/.config/menus  The two main files are *applications.menu* and *settings.menu*. Once again, you can back up these folders/files to restore on the same system but transferring to another machine would be problematic since they reference files such as "alacarte-made-1.desktop".

---

