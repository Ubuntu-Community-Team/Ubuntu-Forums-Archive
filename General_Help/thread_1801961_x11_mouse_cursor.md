---
title: "x11 mouse cursor"
date: 2011-07-11
forum: General Help
---

### Post by linkingeek on 2011-07-11
I have few custom themes available with me for mouse cursor but i have not been able to change anyone of them on Firefox 5.
1. I have tried changing index.theme on following two locations
-usr/share/icons/default/
-home/<usr>/.icons/
2. Also applied through gconf-editor
-by desktop>peripherals>mouse
3. Changed inherits field of x-cursor-theme in etc/alternatives

And the above all methods failed,rest everywhere mouse cursor has been changed but not on firefox content window falls back to DMZ-White

-I have tried to apply following themes
Obsidian
Ecliz-Full

---

### Post by linkingeek on 2011-07-11
Please anyone know how to fix it.:confused:

---

### Post by linkingeek on 2011-07-11
One more thing i'm not using compiz infact it is not installed.
Problems on Natty Narwhal, HP Netbook ,synaptics touchpad.

---

### Post by Jouke74 on 2011-07-11
Use the command:

```

sudo update-alternatives --config x-cursor-theme
```

In the terminal and select the cursor theme that you want to use. 
Note that there might be some cursor themes that are not available for X11, but are available for Gnome.

---

### Post by linkingeek on 2011-07-12
This command shows only few pre-installed cursor not other added cursors

---

