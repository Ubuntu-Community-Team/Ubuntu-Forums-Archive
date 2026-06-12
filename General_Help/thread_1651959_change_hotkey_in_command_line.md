---
title: "change hotkey in command line"
date: 2010-12-24
forum: General Help
---

### Post by gufide on 2010-12-24
I just searching a way to modify a hotkey like in system->preference->keyboard shortcuts but in command line, because I want to make a configuration file and I need to delete a hotkey. anyone?

---

### Post by gufide on 2010-12-24
bump

---

### Post by gufide on 2010-12-25
bump again

---

### Post by BiAiB on 2011-04-03
Here is a sample I use:

```
gconftool-2 --unset /apps/metacity/global_keybindings/switch_to_workspace_7
gconftool-2 --unset /apps/metacity/global_keybindings/switch_to_workspace_8

gconftool-2 -t str --set /apps/metacity/global_keybindings/switch_to_workspace_1 "<Mod4>ampersand"
gconftool-2 -t str --set /apps/metacity/global_keybindings/switch_to_workspace_2 "<Mod4>eacute"
```

to get the name of the command you want to shortcut, you can browse gconf-editor. See: [http://www.howtogeek.com/howto/ubuntu/assign-custom-shortcut-keys-on-ubuntu-linux/](http://www.howtogeek.com/howto/ubuntu/assign-custom-shortcut-keys-on-ubuntu-linux/) .

---

