---
title: "Can't get rid of USA keyboard layout, Ubuntu  10.04 LTS"
date: 2010-09-05
forum: General Help
---

### Post by jjsh on 2010-09-05
As above, whenever I log in, either after boot up or after the screen saver has kicked in, the keyboard reverts to US layout, even if I have manually changed it to GB (UK) layout.

I have tried going into system - preferences - keyboard - layouts and removing US layout, but it keeps reappearing.

Does anyone know how to get rid of this keyboard layout imperialism once and for all? ;)

---

### Post by jjsh on 2010-09-05
OK, I've tried 'remove' of the USA layout in keyboard prefs, then 'apply system wide' and the problem still persists. Any ideas? Is there a file in X i need to edit?

---

### Post by drs305 on 2010-09-05
If you run the following command after making your change via the keyboard preferences, does the entry reflect "gb" ?
```

gconf-editor /desktop/gnome/peripherals/keyboard/kbd/layouts
```

If "gb" isn't the first (leftmost) you can double-click on the values to open up the setting, where you can move it via Up/Down buttons.

If the change doesn't persist, you can also try setting the "gb" keyboard as root with the following command:
```
gksu gconf-editor /desktop/gnome/peripherals/keyboard/kbd/layouts
```

Using gconf-editor normally should mimic the changes you've made via other methods - it's just a different way of doing it.

---

### Post by jjsh on 2010-09-06
Thanks for that. Tried the first option, and GB is listed as the only layout. I then tried the second option, no layout was listed, so I changed this to GB but USA was back again on reboot.

Any ideas?

---

### Post by jjsh on 2010-09-10
Bump

---

### Post by uRock on 2010-09-10
At the login screen you can select different layouts.

---

### Post by nickolasemp on 2010-09-22
The problem is that GDM does not know about the change in default keyboard layout, to fix the problem, log out, change the keyboard layout to the one desired, log back in, then remove the original keyboard layout from keyboard preferences. From now on the us keyboard layout should be gone.

[See the bug here]("https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/530999")

---

### Post by lvleph on 2011-01-19
Thank you nickolasemp. This was really getting annoying.

---

