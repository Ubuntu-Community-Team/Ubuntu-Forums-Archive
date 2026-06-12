---
title: "super key to applications menu"
date: 2011-05-15
forum: General Help
---

### Post by conradin on 2011-05-15
Hi all, 
Im sure this has been discussed, and solved, but I cant find it. I want to use the super key to open the applications menu. If the applications menu is already open, I want the super key to close it. 1 click. how can I get this done?

---

### Post by enimeizoo on 2011-05-15
hello,
I think I found it here. I didn't test yet because I use kde, so no guaranties!
[http://lifehacker.com/5625725/open-the-gnome-applications-menu-with-the-windows-key](http://lifehacker.com/5625725/open-the-gnome-applications-menu-with-the-windows-key)

---

### Post by conradin on 2011-05-15
Thats pretty good. It forces the applications bar menu to drop but doesnt close it if its open already. 

The command was:
```
gconftool-2 --set /apps/metacity/global_keybindings/panel_main_menu --type string "Super_L"
```

---

### Post by enimeizoo on 2011-05-15
What happens if you replace Super_L by Escape?
This should change the shortcut to your escape key, but we will fix it after if it works with the escape key.

The idea is to trigger the menu with escape, and hoping it is closed when you press escape the second time (since escape normally closes it).

---

### Post by conradin on 2011-05-16
Good enough! Thanks enimeizoo!

---

