---
title: "keyboard types wrong key"
date: 2009-12-05
forum: General Help
---

### Post by facejumphead on 2009-12-05
I recently bought an Asus G60 laptop, and I put ubuntu 8.10 on it. The installer has incorrectly identified my keyboard as "generic 105-key (intl) PC", when it should be "generic 104-key PC". Every key works correctly except the pipe / back slash key, which will type greater than / less than instead. If you look at the layout of the "generic 105-key (intl) PC" (system > preferences > keyboard > layout tab > hit the +), the pipe / back slash key is typing that greater than less than key next to the left shift. I tried changing the layout to the correct one, as well as several others, but I can't get this key to work properly. What is the best way to get this key to type pipe / back slash? Is there a program out there that I can use to map the keys properly, or is there a layout I missed?

---

### Post by fluffman86 on 2009-12-05
In System > Preferences > Keyboard, select the keyboard you want to use by make/model instead of just generic.

---

### Post by bunk3rk1ng on 2009-12-05
Check out this post

[https://help.ubuntu.com/6.06/xubuntu/desktopguide/C/switch-keyboard-layout.html](https://help.ubuntu.com/6.06/xubuntu/desktopguide/C/switch-keyboard-layout.html)

Also, if this helps, this is what is in my xorg.conf file regarding my keyboard.

```
Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection
```

---

### Post by facejumphead on 2009-12-06
> **fluffman86 said:**
> In System > Preferences > Keyboard, select the keyboard you want to use by make/model instead of just generic.

I tried picking "Asus" and "Asus Laptop" as the vendor and model of keyboard, but the key still types greater than / less than.

> **bunk3rk1ng said:**
> Check out this post

[https://help.ubuntu.com/6.06/xubuntu/desktopguide/C/switch-keyboard-layout.html](https://help.ubuntu.com/6.06/xubuntu/desktopguide/C/switch-keyboard-layout.html)

Also, if this helps, this is what is in my xorg.conf file regarding my keyboard.

```
Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection
```

It looks like this was written before the preferences utility was created for changing keyboard layouts. I don't have any sections on layout in there. My xorg.conf looks like it is set up correctly to me (I have the same thing in there you do.)

```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

```

---

### Post by facejumphead on 2009-12-06
I found a sort-of fix for this, and I wanted to post it in case anyone else could benefit.

It looks like this has been an issue for other distros as well, and other laptops in the same line as mine. I found this page:

[http://forum.notebookreview.com/showthread.php?t=405784](http://forum.notebookreview.com/showthread.php?t=405784)

I didn't see anything like the us.map.gz, like they say in the instructions, but putting the .Xmodmap file with this in it:```
keycode 94 = backslash bar
```in my home directory worked for me. Next time I booted my laptop, it asked if I wanted to load the Xmodmap file, and after that the pipe key works just fine while I am in gnome (almost 100% of the time). I assume that this will only work for my user, since the .Xmodmap is in my home directory. It also doesn't work if I hit ctrl + alt + f1 to get to the console. It would probably also be very bad if I used one of my passwords with a pipe in it as a login password, since I don't think I would be able to type that at the login screen. But 99% of the problem is addressed with the Xmodmap file.

---

### Post by Handle on 2010-11-22
In 10.10 this problem can be corrected by going to *System > Preferences > Keyboard, Layouts* tab and setting *keyboard model*. For me, the right model is *Classmate PC*. After selecting the keyboard model, click *Apply System-Wide*.

---

### Post by xVehemencityx on 2011-10-18
Sorry to revive a dead thread, but I'm experiencing the same problem, on the same laptop.  I'm using 11.10.  Changing keyboard layout doesn't work.  11.10 gnome 3 doesn't really let me change much graphically, and I can't find the file manually.

---

### Post by DreymaR on 2011-10-19
Indeed - where's the Keyboard Model setting option gone to?!? I need that.

---

