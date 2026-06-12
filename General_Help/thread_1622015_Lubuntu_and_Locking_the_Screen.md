---
title: "Lubuntu and Locking the Screen"
date: 2010-11-14
forum: General Help
---

### Post by Captain Smiley Pants on 2010-11-14
Hey guys, how can I lock my session? CTRL + ALT + L isn't working out for some reason.

---

### Post by sisco311 on 2010-11-15
Lubuntu uses xscreensaver, so you have to create a keyboard shortcut for:
```
xscreensaver-command -lock
```

Edit the ~/.config/openbox/lubuntu-rc.xml file and add something like:
```
<keybind key="C-A-l">
    <action name="execute">
        <command>xscreensaver-command -lock</command>
    </action>
</keybind>
```

---

