---
title: "How do I remove this keybind?"
date: 2011-11-04
forum: General Help
---

### Post by Charkel on 2011-11-04
Hello.
Yesterday I wanted to bind ctrl + alt + del to the system monitor. So after a quick goolesearch i found this:
```

gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9"<Control><Alt>Delete"
gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-system-monitor"
```
That did not work so I quit trying. Instead today i found out that i had managed to bind it to delete! So now I cannot use delete :(

How can i revert this?

Thank you.

---

### Post by Charkel on 2011-11-10
BUMP because of page 60+

---

