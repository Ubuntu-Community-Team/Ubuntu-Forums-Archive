---
title: "Custom keyboard shortcut doesn't work"
date: 2009-10-25
forum: General Help
---

### Post by Aero-Z on 2009-10-25
Hello,

I wanted to have a shortcut to open system monitor. So I did:
```
gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<Control><Shift>Escape"
gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-system-monitor"

```
I also tried it in gconf GUI but it still doesn't work.

Any ideas?

---

### Post by dv3500ea on 2009-10-25
Try going into system->preferences->keyboard shortcuts

---

### Post by Aero-Z on 2009-10-25
> **dv3500ea said:**
> Try going into system->preferences->keyboard shortcuts
Worked. Thanks :)

---

