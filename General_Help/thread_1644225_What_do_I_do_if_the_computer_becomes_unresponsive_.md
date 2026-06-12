---
title: "What do I do if the computer becomes unresponsive to mouse clicks?"
date: 2010-12-13
forum: General Help
---

### Post by MollyWop on 2010-12-13
I'll move around the mouse and see that docky is moving around (computer is not frozen, nautilius desktop environment is unresponsive) how do i fix this without restarting the computer.

---

### Post by Rodney9 on 2010-12-13
Use your keyboard , alt ctrl, delete and reboot.

Check your mouse conection.
Try another mouse.

---

### Post by MollyWop on 2010-12-13
the mouse works, the computer becomes unresponsive. its like it all works, but it doesnt. i was just restoring some files and the shell crashed again..

---

### Post by jocko on 2010-12-13
You could try to restart xorg.
Either press Alt+Ctrl+SysRq to force it to restart, or press Alt+Ctrl+F1 to get to a terminal, log in and run:
```
sudo service gdm restart
```With both of these ways you will loose any unsaved data in open files, so perhaps there is a better way...

---

### Post by MollyWop on 2010-12-13
> **jocko said:**
> You could try to restart xorg.
Either press Alt+Ctrl+SysRq to force it to restart, or press Alt+Ctrl+F1 to get to a terminal, log in and run:
```
sudo service gdm restart
```With both of these ways you will loose any unsaved data in open files, so perhaps there is a better way...
I just pressed alt ctrl f1 while my computer was restoring some files using deja dup and it happened again...

---

