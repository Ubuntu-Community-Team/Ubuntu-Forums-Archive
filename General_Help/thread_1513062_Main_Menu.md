---
title: "Main Menu"
date: 2010-06-18
forum: General Help
---

### Post by pwaugh on 2010-06-18
Hey, I noticed that in addition to the regular main menu that is active by default, there one that is just the Ubuntu symbol.  Unfortunately, that one has a bug with the scrolling of the menus, which I can't even report since I have no idea how.

But, my real question is, I notice that at one time, the menu had the Gnome "foot" as a symbol.  I'd love to have the option of having the foot.  So, is there a version that has it, I can download?  Or, could someone point me to the source so I can make my own mod?

Patrick

---

### Post by Tim Sharitt on 2010-06-18
The menu icon is set by the icon theme being used (I think it is {icon-dir}/places/distributor-logo.svg but I'm not sure) which happens to be the ubuntu logo in ubuntu. Generic gnome themes use the gnome logo. You could swap the gnome foot for the ubuntu logo in your theme, but that would change the icon where ever else that icon is used.

---

### Post by pwaugh on 2010-06-18
Thanks.  I really don't want to switch it everywhere... so I'll just leave it.  Just seemed like since I'm using the Gnome desktop it might be cool.  I'll settle for a wallpaper.  The ubuntu icon is cool too.  :)

---

### Post by kerry_s on 2010-06-18
in gconf-editor(look under apps-> panel), you can set a custom icon for the main menu.

i'm not running a menu so i can't tell you the exact steps, but if you look you'll see it.

---

### Post by pwaugh on 2010-06-18
> **kerry_s said:**
> in gconf-editor(look under apps-> panel), you can set a custom icon for the main menu.

i'm not running a menu so i can't tell you the exact steps, but if you look you'll see it.

Oh, awesome, I'll check into it.

---

### Post by pwaugh on 2010-06-18
> **kerry_s said:**
> in gconf-editor(look under apps-> panel), you can set a custom icon for the main menu.

i'm not running a menu so i can't tell you the exact steps, but if you look you'll see it.

FYI, although I found the "object" and entered a custom icon and enabled it, it won't work for objects of type "menu-bar", so you can't modify the icon used using gconf-editor as far as I can tell.  But was worth a try.  :)

---

### Post by kerry_s on 2010-06-19
> **pwaugh said:**
> FYI, although I found the "object" and entered a custom icon and enabled it, it won't work for objects of type "menu-bar", so you can't modify the icon used using gconf-editor as far as I can tell.  But was worth a try.  :)

bummer, use to work.
how about:
```
sudo update-alternatives --config start-here.svg
```

if you don't mind the terminal.

---

### Post by pwaugh on 2010-06-19
> **kerry_s said:**
> bummer, use to work.
how about:
```
sudo update-alternatives --config start-here.svg
```

if you don't mind the terminal.

Interesting.  I tried that and selected the gnome foot, but didn't see a change in the menu.

```

patrick@laptop:~$ sudo update-alternatives --config start-here.svg
There are 4 choices for the alternative start-here.svg (providing /usr/share/icons/gnome/scalable/places/start-here.svg).

  Selection    Path                                                     Priority   Status
------------------------------------------------------------
  0            /usr/share/icons/gnome/scalable/places/ubuntu-logo.svg    60        auto mode
  1            /usr/share/icons/gnome/scalable/places/debian-swirl.svg   30        manual mode
* 2            /usr/share/icons/gnome/scalable/places/gnome-foot.svg     20        manual mode
  3            /usr/share/icons/gnome/scalable/places/swirl-foot.svg     20        manual mode
  4            /usr/share/icons/gnome/scalable/places/ubuntu-logo.svg    60        manual mode

Press enter to keep the current choice[*], or type selection number: 

```

Was worth a shot though, and learned something new about the system.

patrick

---

### Post by kerry_s on 2010-06-19
man, they just change everything & leave the old stuff in place to tease us. :lolflag:

from what you posted it looks like its setup to only work with the default gnome theme.

i'm out of ideas, other then manual editing.

---

