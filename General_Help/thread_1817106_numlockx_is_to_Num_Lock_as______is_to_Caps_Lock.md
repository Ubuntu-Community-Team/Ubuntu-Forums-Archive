---
title: "numlockx is to Num Lock as ____ is to Caps Lock"
date: 2011-08-02
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2011-08-02
Fill in the blank any ideas
command needed to turn caps lock on/off

i am trying to rig a little something to make caps lock require a modifier to work
so far this is what i have
```
#!/bin/sh
OFF="[caps    caps:none]"
ON="[]"
STATE=$(gconftool --get /desktop/gnome/peripherals/keyboard/kbd/options)
if [ "$STATE" = "$ON" ]; then
    gconftool --set "/desktop/gnome/peripherals/keyboard/kbd/options" --type list --list-type=string "$OFF"
else
    gconftool --set "/desktop/gnome/peripherals/keyboard/kbd/options" --type list --list-type=string "$ON"
fi
```To clarify i want a equivalent of this command for caps lock
```
numlockx toggle
```

---

### Post by idoitprone on 2011-08-03
```
! xmodmap file
! for me only linux blah
 
! Swap Caps_Lock and Escape
 
 
remove Lock = Caps_Lock
remove Mod1 = Escape
keysym Escape = Caps_Lock
keysym Caps_Lock = Escape
clear Lock
add Lock = Caps_Lock
add Mod1 = Escape

```
This script swap caps lock and escape key
save it in a file
then do```
 xmodmap file
```

this links show another method
[https://wiki.archlinux.org/index.php/Xorg#Keyboard_settings](https://wiki.archlinux.org/index.php/Xorg#Keyboard_settings)

---

### Post by pqwoerituytrueiwoq on 2011-08-03
i don't want to swap them
i just need a terminal command to turn caps lock on and off (the keyboard light)
i blank to disabled caps lock and use Shift+VoidSymbol to toggle caps lock
Caps Lock = void
Caps Lock + Shift = Standard Caps Lock Behavior

---

### Post by idoitprone on 2011-08-05
> **pqwoerituytrueiwoq said:**
> i don't want to swap them
i just need a terminal command to turn caps lock on and off (the keyboard light)
i blank to disabled caps lock and use Shift+VoidSymbol to toggle caps lock
Caps Lock = void
Caps Lock + Shift = Standard Caps Lock Behavior

I do not know how to mess around with the modifer keys, but the command to turn off caps lock is
```

 setxkbmap -option caps:none
```

---

### Post by ealfonso on 2013-02-22
What you want is:

```
xmodmap -e 'keycode 66 = NoSymbol Caps_Lock'
```

---

