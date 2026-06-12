---
title: "Ctrl+Alt+T doesn't work anymore"
date: 2012-03-20
forum: General Help
---

### Post by justanoob on 2012-03-20
Running Ubuntu 11.10.

I've checked keyboard shortcuts, which shows Ctrl+Alt+T as the shortcut for a terminal. The only thing I changed was playing around with Compiz Fusion Settings. Something got borked up (still not sure exactly what). Got everything back to normal except (from what I can tell so far) launching terminal from the keyboard. I can launch it from the menu, just not Ctrl+Alt+T.

---

### Post by sudodus on 2012-03-20
There is a menu where to add, change or delete ***keyboard shortcuts***. Probably it has been changed. Can you find that menu, and check it?

---

### Post by codemaniac on 2012-03-20
you can get a list of all the key bindings gconf keys by looking in the files located in /usr/share/gnome-control-center/keybindings/ .

Haev a look at the xml file /usr/share/gnome-control-center/keybindings/01-desktop-key.xml , which lists keys for all the shortcuts Keyboard Shortcuts lists under Desktop .

if you want to change shortcut for a specific application .run something like below .
```
gconftool -u "/apps/gnome_settings_daemon/keybindings/application_name"
```

---

### Post by justanoob on 2012-03-24
Thanks for the help, folks. It's working again.

---

### Post by Flywaver on 2012-03-29
> **codemaniac said:**
> you can get a list of all the key bindings gconf keys by looking in the files located in /usr/share/gnome-control-center/keybindings/ .

Haev a look at the xml file /usr/share/gnome-control-center/keybindings/01-desktop-key.xml , which lists keys for all the shortcuts Keyboard Shortcuts lists under Desktop .

if you want to change shortcut for a specific application .run something like below .
```
gconftool -u "/apps/gnome_settings_daemon/keybindings/application_name"
```

For some reason I don't have this 01-desktop-key.xml file...and when I check in Settings > Keyboard > Shortcuts...Launch Terminal is set to CTRL+ALT+T! :confused:

---

### Post by bobman321123 on 2012-03-29
Just make a new shortcut in System settings>keyboard>shortcuts>custom>*hit-the-plus-sign*
Then name it whatever you want, and in "command" enter "gnome-terminal". 
Double click it, press the keyboard combo you want, and it should give you an error message about the default terminal keybinding, but just ignore it and hit ok. 
Voila, that worked for me.

---

### Post by Flywaver on 2012-03-29
> **bobman321123 said:**
> Just make a new shortcut in System settings>keyboard>shortcuts>custom>*hit-the-plus-sign*
Then name it whatever you want, and in "command" enter "gnome-terminal". 
Double click it, press the keyboard combo you want, and it should give you an error message about the default terminal keybinding, but just ignore it and hit ok. 
Voila, that worked for me.

Thanks!!! it worked! :)

---

### Post by bobman321123 on 2012-03-29
No problem :)

---

