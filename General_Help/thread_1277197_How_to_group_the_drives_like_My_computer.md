---
title: "How to group the drives like My computer"
date: 2009-09-28
forum: General Help
---

### Post by lgjsheron on 2009-09-28
How to group drives in a one place like My Computer in Windows and avoid the drive icons in the desktop.

---

### Post by nothingspecial on 2009-09-28
Press Alt+F2 and type ```
gconf-editor
```

I think the path is apps > nautilus > desktop

anyway, somewhere in there is an option called volumes_visible or something like that. If you un check it the drive icons will disappear from your desktop.

Sorry to be so vague - not using gnome right now so I can`t check.

---

### Post by 3rdalbum on 2009-09-28
nothingspecial has an excellent memory. You will also want to check "computer_icon_visible".

I personally can't live without the drives on the desktop, it saves me a double-click each time.

---

### Post by scouser73 on 2009-09-28
To Hide the mounted drive icons on your desktop please follow these instructions.

**1** - Press **Alt & F2** and enter this command: **gconf-editor**

**2** - Now browse down to the following key: **apps \ nautilus \ desktop**

**3** - You should see a key in the right-hand pane called **volumes_visible**. Remove the checkbox from it, and the icons will instantly disappear from the desktop. Remember that you can always access the drives from the “Computer” icon, or easily in the file browser.

---

