---
title: "keyboard shortcut (run in terminal)"
date: 2010-10-24
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2010-10-24
anyone know a way to make a keyboard shortcut run in terminal

---

### Post by bashphoenux on 2010-10-24
run "gconf-editor" and look up /apps/metacity/keybinding_commands. Set  "command_1" to "gnome-terminal", and then go to  /apps/metacity/global_keybindings, and set "run_command_1" to the key  you want, using the same format as the other entries.

---

### Post by pqwoerituytrueiwoq on 2010-10-24
perhaps i should rephrase
i want to run myFile.sh in a terminal on a key control

---

### Post by bashphoenux on 2010-10-24
> **bashphoenux said:**
> run "gconf-editor" and look up  /apps/metacity/keybinding_commands. Set  "command_1" to  "gnome-terminal", and then go to  /apps/metacity/global_keybindings, and  set "run_command_1" to the key  you want, using the same format as the  other entries.
in the above mentioned steps :
Set  "command_1" to "gnome-terminal -x sh /path to your script"

---

