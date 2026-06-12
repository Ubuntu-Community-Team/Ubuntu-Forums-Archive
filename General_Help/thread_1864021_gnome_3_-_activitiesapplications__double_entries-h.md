---
title: "gnome 3 - activities:applications  double entries-horrid icons"
date: 2011-10-18
forum: General Help
---

### Post by SE7EN-LOCSTA on 2011-10-18
[ubuntu 11.10 x64] today, while installing icon themes and gnome (The GNOME Desktop Environment, with extra components) i was in applications, and noticed that alot of my programs were doubled, one from the icon package i have selected, and another one, a low quality one (doesnt change when change icon set). i went to the main menu customizer, and deselected everything, but nothing changed. i uninstalled the gnome package, restarted, nothing changed. 

i went through, thinking that it 'had' to be the dependencies programs that the gnome package needed, but they dont match up. 'cheese' is on the list, but not doubled; audacious and audacity are not on the list, but are doubled. a few of them have differing names, such as "firefox browser' [lq] and 'firefox web browser' [hq]. 

the inability to change what items appear in your menus is a major issue from gnome2 to unity/gnome 3 for me, especially now that i have an extra few dozen duplicates (of very bad quality) in my menu.

anyone got ideas on how to remove these duplicates, or maybe even a way to choose what gets placed in your menus?


edit: uninstalling a (double icon) program fixes it. reinstalling it does not cause doubles to reappear.

---

### Post by AvalonSpirit on 2011-10-18
I have the same thing happening, there has to be a better way to solve the issue than uninstalling and reinstalling aplications

---

### Post by crdlb on 2011-10-18
You can edit the list of applications in [alacarte](apt:alacarte), the gnome menu editor. You could also look in /usr/share/applications/ and ~/.local/share/applications/ for duplicates. Note that a .desktop file in the latter will override one with the same name in the former. Alacarte edits the menu by creating those overrides.

---

### Post by AvalonSpirit on 2011-10-19
thanks, crdlb i'll look into alacarte. Meanwile i found where my duplicates were coming form. I used the main menu editor, and appparently when i installed gnome 3 the debian menu loaded al the aplications again, by unchecking the boxes there and leaving the boxes in the other ubuntu menus checked I managed to get rid of the duplicates with the low resolution icons.

Edit: I just realized that alacarte IS the main menu editor (the one i used)... oops... anyway, it worked! thanks crdble!

---

### Post by SE7EN-LOCSTA on 2011-10-20
i have also located the source of my problems. 'menu-xdg'

i had installed it with the gnome extras package, and it was the reason behind my entries being doubled for some items. removing this package fixes problem. 

unistalling/reinstalling a doubled menu item does appear to fix it, but upon a relog, the doubles returned.

---

### Post by stewacide on 2011-11-04
Just installed the 'gnome' package on 11.10 (Gnome 3 is much easier for my mom to understand than Unity) and ran into the same problem. Removing menu-xdg did the trick, but it's annoying this bug still exists.

---

