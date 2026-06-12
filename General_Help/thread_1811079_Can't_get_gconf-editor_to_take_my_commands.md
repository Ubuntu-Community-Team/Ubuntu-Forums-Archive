---
title: "Can't get gconf-editor to take my commands"
date: 2011-07-24
forum: General Help
---

### Post by lagu2653 on 2011-07-24
I tried [http://www.howtogeek.com/howto/ubuntu/assign-custom-shortcut-keys-on-ubuntu-linux/]("http://www.howtogeek.com/howto/ubuntu/assign-custom-shortcut-keys-on-ubuntu-linux/").
I opened Alt-F2 > gconf-editor > metacity and used command_1 in keybinding_commands. The type was string and the value xterm. I then moved to global_keybindings and used run_command_1. The value was now <Control><Alt><Shift>p. Nothing happens when I press the key combination. I've tried other key combinations also. And I've tried to run root as root and as user. rebooted. Nothing happens. If I change an existing key combination it takes it immediately an xterm pops up.

---

### Post by CatKiller on 2011-07-24
In all likelihood, Metacity isn't your window manager; Compiz is.

---

