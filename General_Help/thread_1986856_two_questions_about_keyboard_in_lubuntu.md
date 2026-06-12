---
title: "two questions about keyboard in lubuntu"
date: 2012-05-25
forum: General Help
---

### Post by MeriMeri on 2012-05-25
[FONT=Tahoma]Hi there!
im using lubuntu 11.10 and have two questions about it.

the first one:
there is an app that locks the screen (ScreenLock). i want to define a keyboard shortcut for it. how can i do it?
for example, i want to lock the screen using Super + L

--------------------------------------------

second:
i use Bulgarian as the second language on keyboard (beside English US). for switching between these two, i use a code in terminal.
the problem is, it change from English to Bulgarian with right Shift, but from Bulgarian to English with left Shift.
i want both with right one. what should i do??

and one more: can i call this code (for switching keyboards layout) automatically when i login to lubuntu??

thank you all in advance
[/FONT]

---

### Post by mikewhatever on 2012-05-25
The default shortcut to lock the screen is ctrl-alt-l. If you have to change it, there is probably an XML file to dig through, I am not sure.

The way you switch keyboard layouts is really odd. Is that intentional? Why not let a key (or a key combination) cycle through them, after all, there are only two.

Just add something like the following to the .bashrc in your home folder, and then run source ~/.bashrc:

setxkbmap -option grp:ctrl_shift_toggle us,bl

I don't really know what's the keyboard code for Bulgarian (assumed it's bl), please change it to the correct one. Needless to say, you can also modify the layout switching keys.

---

### Post by MeriMeri on 2012-05-26
> **mikewhatever said:**
> The default shortcut to lock the screen is ctrl-alt-l. If you have to change it, there is probably an XML file to dig through, I am not sure.

The way you switch keyboard layouts is really odd. Is that intentional? Why not let a key (or a key combination) cycle through them, after all, there are only two.

Just add something like the following to the .bashrc in your home folder, and then run source ~/.bashrc:

setxkbmap -option grp:ctrl_shift_toggle us,bl

I don't really know what's the keyboard code for Bulgarian (assumed it's bl), please change it to the correct one. Needless to say, you can also modify the layout switching keys.

thanks for your response mikewhatever,
ctrl + alt + l is for gnome (in Ubuntu). im using Lubuntu, so that shortcut doesnt work under lubuntu. (we have to make lock app ourself, its not ready to use like ubuntu)

unfortunately in Lubuntu there is a full of bug software for changing keyboard layout. so every time we login to lubuntu, we have to call this code to active the second language.

i was read it somewhere else that i have to put the code in .bashrc and i did it but nothing happened after restart. ( didnt run, just saved it)

by the way, its the code (in terminal) for changing layouts:
```
setxkbmap -layout "us,bl" -option "grp:alt_shift_toggle"
```

---

### Post by MeriMeri on 2012-05-26
using guides in the following page, two of the problems solved:
[https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides](https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides)

1- i assigned a shortcut for locking the screen with super+l
2- now my settings for keyboard layout loads automatically.

[SIZE=2][B]but still a problem:
i want switch between layouts, both with Right shift.
what should i do for this one??[/B][/SIZE]

---

### Post by mikewhatever on 2012-05-26
Ctrl-alt-l works for me in Lubuntu 12.04, as well as the keyboard layout switching method.

---

