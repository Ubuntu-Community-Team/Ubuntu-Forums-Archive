---
title: "How do I replace missing applets?"
date: 2011-03-05
forum: General Help
---

### Post by Rgibbons on 2011-03-05
After doing one of the security upgrades on Maverick I discovered several of my applets were missing:

system tray
network manager
restart/shutdown
etc.

Anyone know how I can restore these?

---

### Post by Frogs Hair on 2011-03-05
One way is to right click the panel > add to panel and add what you need from the menu. It sounds like you are missing the notification area and indicator applet session .

You can attempt to reset panels to defaults by running this command in the terminal.```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```

---

### Post by Rgibbons on 2011-03-05
Your my hero! That did the trick. So nice to be able to use Linux again.

---

