---
title: "Some issues with Xfce4.10"
date: 2012-05-12
forum: General Help
---

### Post by u-noob-tu on 2012-05-12
I recently switched over to Xfce from GNOME-Shell and I am really enjoying it, and yesterday I updated to Xfce 4.10. I seem to have a few issues with it though. For one, alacarte (the GNOME main menu editor) seems to crash whenever i make changes to it. I am unable to add items or separators, i can only remove items. Nothing happens when i hit "New Item". Secondly, Gwibber asks for a keyring unlock each time i start it. Im not sure why. Has anyone experienced these issues?

EDIT: Also, chromium seems to have the same issue as gwibber. asks for a keyring.

---

### Post by zugol on 2012-05-14
Hi!

Same issue for me with Alacarte. The same error message can be found in old launchpad tickets. The problem was linked to a gnome-panel dependency but I don't try because in xubuntu 12.04 this workaround will install the whole gnome-fallback desktop...

---

### Post by Bucky Ball on 2012-05-14
Think OP already has Gnome-fallback (shell) installed so the fix you suggest might work if you have a link.

---

### Post by jefsview on 2012-05-14
You need to ask in the Xfce forums firstly, since 12.04 doesn't officially support Xfce 4.10. 12.10 will be the first Xubuntu release to support Xfce 4.10, due to 12.04 being frozen when the latest Xfce was released.

Also, as an aside, Alacarte has never fully worked with Xfce. It was a nice idea to try and integrate a menu editor, but Alacarte never fully worked with Xfce 4.8 either. 

the [Lxmenu editor]("http://lxmed.sourceforge.net/")  works much better and isn't prone to crashing like Alacarte. 

-- Jeff

---

### Post by Bucky Ball on 2012-05-14
> **jefsview said:**
>  

... the [Lxmenu editor]("http://lxmed.sourceforge.net/")  works much better and isn't prone to crashing like Alacarte. 

-- Jeff

... and also seems to be for Lxde rather than Xfce by the looks of the webpage. Or will it work on either? Thinking you might need to drag in a heap of Lxde stuff to get it happening on xfce.

---

### Post by Toz on 2012-05-14
Have a look at ~/.xsession-errors when you try to create a new item. It appears to be looking for gnome-desktop-item-edit. (If you look at the actual code, you'll see that its trying to evaluate XDG_CURRENT_DESKTOP and not returning the proper value). gnome-desktop-item-edit is part of gnome-panel. If you don't have gnome-panel installed and don't want to pull in all of those extra gnome dependencies, you have 2 possible workarounds:

1. (the one I tested) Simply link gnome-desktop-item-edit to exo-desktop-item-edit:
```
sudo ln -s /usr/bin/exo-desktop-item-edit /usr/bin/gnome-desktop-item-edit
```
2. (in theory this should work) Set XDG_CURRENT_DESKTOP=XFCE as a global environment variable

---

### Post by u-noob-tu on 2012-05-14
> **Toz said:**
> Have a look at ~/.xsession-errors when you try to create a new item. It appears to be looking for gnome-desktop-item-edit. (If you look at the actual code, you'll see that its trying to evaluate XDG_CURRENT_DESKTOP and not returning the proper value). gnome-desktop-item-edit is part of gnome-panel. If you don't have gnome-panel installed and don't want to pull in all of those extra gnome dependencies, you have 2 possible workarounds:

1. (the one I tested) Simply link gnome-desktop-item-edit to exo-desktop-item-edit:
```
sudo ln -s /usr/bin/exo-desktop-item-edit /usr/bin/gnome-desktop-item-edit
```
2. (in theory this should work) Set XDG_CURRENT_DESKTOP=XFCE as a global environment variable

I tried your first solution, and i can now add things (at least as far as i tested, i only had a few minutes to try it before i had to go to class), though i still couldnt add a separator. for the record, i do not have gnome-fallback installed. ill try your second suggestion when i get back to my computer.

---

### Post by zugol on 2012-05-14
The "ln" solution works like a charme !!!

A lot of thanks !!

---

