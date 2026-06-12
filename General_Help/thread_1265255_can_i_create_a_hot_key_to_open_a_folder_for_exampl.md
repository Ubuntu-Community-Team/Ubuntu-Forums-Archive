---
title: "can i create a hot key to open a folder? for example"
date: 2009-09-13
forum: General Help
---

### Post by talphp on 2009-09-13
CTRL + SHIFT + F11 -> open me /var/www/ ?

---

### Post by m_duck on 2009-09-13
I'm not on an Ubuntu box atm, but I think this is possible. There should be a "Keyboard Shortcuts" option (or similar) in the System -> Preferences menu. If you scroll to the bottom, then click add, you should be able to choose a key combo such as the one you mentioned to run the command: ```
nautilus /var/www
```If the permissions are still as standard on that folder and root access is needed, try the prefixing the above with gksu:```
gksu nautilus /var/www
```

---

### Post by geirha on 2009-09-13
The ability to add custom commands with keyboard shortcuts was removed from the gui for some reason. The ability is still there though, and you can set it up with gconf-editor. Run «gconf-editor» and browse to /apps/metacity/. Add your custom commands under keybinding_commands, and set the keyboard shortcuts under global_keybindings.

As m_duck mentions, if you set the command to «nautilus /var/www» it will open that folder in nautilus. You can also use «xdg-open /var/www» which will use whichever program is the default for opening directories (which in Ubuntu with gnome, is nautilus).

---

### Post by newsoft on 2009-09-13
I think not available anymore

---

### Post by talphp on 2009-09-24
> **geirha said:**
> The ability to add custom commands with keyboard shortcuts was removed from the gui for some reason. The ability is still there though, and you can set it up with gconf-editor. Run «gconf-editor» and browse to /apps/metacity/. Add your custom commands under keybinding_commands, and set the keyboard shortcuts under global_keybindings.

As m_duck mentions, if you set the command to «nautilus /var/www» it will open that folder in nautilus. You can also use «xdg-open /var/www» which will use whichever program is the default for opening directories (which in Ubuntu with gnome, is nautilus).

Thanks man!! you helped me alot! [solved]

---

