---
title: "Show Desktop (Not Windows Key + D)"
date: 2012-07-29
forum: General Help
---

### Post by barrdakota on 2012-07-29
How do I change the show desktop feature back to Windows Key + D? Ubuntu suddenly changed it to CTRL + ALT + D when I upgraded.

This is probably the most annoying change I have ever experienced with Ubuntu. Anybody know a fix?

---

### Post by sakamoto on 2012-07-29
System > Preferences > Keyboard shortcuts

then look for 'Hide all normal windows and set focus to the desktop'

---

### Post by barrdakota on 2012-07-29
> **sakamoto said:**
> System > Preferences > Keyboard shortcuts

then look for 'Hide all normal windows and set focus to the desktop'


That's not possible.

When I go to my keyboard shortcuts, I have to click on the one that I have to change and then hold down the keys that I want to change it to.

However, whenever I click on the Windows Key, it starts a search.

---

### Post by sakamoto on 2012-07-29
run application dialog with Alt+F2 and run below code

```
gconftool-2 --set /apps/metacity/global_keybindings/panel_main_menu --type string "Super_L"
```

windows key will now be recognized in order to use it as a key shortcut.you can test it by just tapping windows key which should open panel application menu

---

