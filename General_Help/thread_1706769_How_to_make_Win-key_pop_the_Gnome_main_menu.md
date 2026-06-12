---
title: "How to make Win-key pop the Gnome main menu"
date: 2011-03-14
forum: General Help
---

### Post by Rebelli0us on 2011-03-14
In System > Preferences > Keyboard shortcuts, it does not allow you to change Alt+F1 to just Mod4. 

Or is there a command that will open the Gnome main menu?

---

### Post by ajgreeny on 2011-03-14
My right hand windows key does that, and I think it did at install, though it is possible I may have edited the keyboard shortcuts (to "Super R") and just have forgotten about it.

I have the left hand windows key mapped to several compiz window-actions, so it can not be used for the main menu in my case.

---

### Post by Zevaka on 2011-03-14
[http://www.howtogeek.com/howto/27038/use-the-windows-key-for-the-start-menu-in-ubuntu-linux-10.04/](http://www.howtogeek.com/howto/27038/use-the-windows-key-for-the-start-menu-in-ubuntu-linux-10.04/)
did it on my previous ubuntu installation, worked flawlessly

---

### Post by Rebelli0us on 2011-03-14
> **Zevaka said:**
> [http://www.howtogeek.com/howto/27038/use-the-windows-key-for-the-start-menu-in-ubuntu-linux-10.04/](http://www.howtogeek.com/howto/27038/use-the-windows-key-for-the-start-menu-in-ubuntu-linux-10.04/)
did it on my previous ubuntu installation, worked flawlessly

Thank you, that works but it destroys all other existing Winkey+ shortcuts, like Win+D (Desktop), Win+E, Win+F, etc.


... but for anyone that wants to do it anyway, this will assign the LEFT Winkey:

```
gconftool-2 --set /apps/metacity/global_keybindings/panel_main_menu --type string "Super_L"
```

and this for the RIGHT Winkey

```
gconftool-2 --set /apps/metacity/global_keybindings/panel_main_menu --type string "Super_R"
```

---

