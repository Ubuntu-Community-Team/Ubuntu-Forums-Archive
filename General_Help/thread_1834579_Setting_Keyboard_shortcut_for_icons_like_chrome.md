---
title: "Setting Keyboard shortcut for icons like chrome"
date: 2011-08-27
forum: General Help
---

### Post by rajohns08 on 2011-08-27
how do i do this?

---

### Post by rajohns08 on 2011-08-28
figured it out for metacity:

1. right click the icon and click properties and copy what is in the command field
2. hit alt+f2
3. type gconf-editor
4. click apps
5. click metacity
6. under global_keybindings pick a command that  isn't being used and type a key combination under value
7. under keybinding_commands paste the command you copied in step 1 into the value field of a command you set a keybinding for

---

