---
title: "Where do the keyboard shortcuts get saved?"
date: 2011-11-12
forum: General Help
---

### Post by aropop on 2011-11-12
I'm devloping an application and i need to know where the keybindings get saved in ubuntu 11.10. I found some shortcuts in gconf but the volume shortcuts aren't there. So my question is where is the config file where the volume key bindings are stored?
Greetz Aropop

---

### Post by crdlb on 2011-11-12
Open dconf-editor (not gconf), and go to org.gnome.settings-daemon.plugins.media-keys. If you want to change those settings from the terminal, use the 'gsettings' command.

The settings are stored on disk at ~/.config/dconf/user, but that is a binary database.

---

### Post by aropop on 2011-11-13
Thanks alot!!

---

