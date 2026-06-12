---
title: "Windows (Super) Key doesn't work... AT ALL"
date: 2012-01-30
forum: General Help
---

### Post by VanceVEP72 on 2012-01-30
I have a fresh install of Xubuntu 11.10 installed and according to the system settings, <Super>p is supposed to be a shortcut to the display settings and <Super>Tab is supposed to switch windows. Neither key-combo works for some reason. It appears that Xubuntu doesn't even recognize the <Super> key on my machine? I am using a Logitech wireless keyboard and my Keyboard is set to Generic 104-key pc. Any ideas? I want to be able to open the Menu with a <Super> shortcut.

---

### Post by kurt18947 on 2012-01-30
Correct, Xubuntu and Lubuntu don't recognize the windows/super key. Ubuntu-Unity and Gnome-shell do.

---

### Post by LewisTM on 2012-01-30
My Xubuntu machines all recognize the Super key, I use it all the time!

Perhaps you should try other keyboard setups? I see entries for lots of Logitech cordless keyboards.

A wild guess: make sure the gnome-settings-daemon is NOT running. It might be grabbing the Super key and preventing its use in Xfce.

---

### Post by LewisTM on 2012-01-30
Okay, to be more precise:
1) <Super>p doesn't work because it calls 'xfce4-display-settings --minimal' which fails because --minimal does not display anything. Just remove the --minimal part and it should work.
2) <Super>Tab switches between windows of the same application. Try it in multiple File Manager windows.
3) <Super> alone is not grabbed by Xfce, it's only a modifier key. Try to bind something like <Super>m to the command 'xfce4-popup-applicationsmenu'

Cheers!

---

### Post by hooliator on 2012-06-26
Thank you Lewis!
I entered the command 'xfce4-popup-applicationsmenu'

then for the shortcut, I hit only the super key and it took it. Xubuntu assigned it as "Super_L"

Now I hit the super key all by itself and the applications menu drops.

---

