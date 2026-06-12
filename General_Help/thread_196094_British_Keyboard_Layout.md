---
title: "British Keyboard Layout"
date: 2006-06-13
forum: General Help
---

### Post by Stormx on 2006-06-13
I want a british keyboard layout. Thats what my keyboard is like. i've had a look in keyboard under preferences, and i have 2 options under @United Kingdom@ <-- look there it goes again.

Dvorak
Some international one which makes beeping noises and only prints some characters


any ideas?

---

### Post by Horizon on 2006-06-13
[QUOTE=Stormx]I want a british keyboard layout. Thats what my keyboard is like. i've had a look in keyboard under preferences, and i have 2 options under @United Kingdom@ <-- look there it goes again.

Dvorak
Some international one which makes beeping noises and only prints some characters


any ideas?[/QUOTE]
You don't have to chose a subcategory, you can just highlight United Kingdom and click add :/
That's what I did anyway.

---

### Post by REBELinBLUE on 2006-06-13
[QUOTE=Stormx]I want a british keyboard layout. Thats what my keyboard is like. i've had a look in keyboard under preferences, and i have 2 options under @United Kingdom@ <-- look there it goes again.

Dvorak
Some international one which makes beeping noises and only prints some characters


any ideas?[/QUOTE]

Rather than expanding the "united kingdom" item, just select that and click OK. That is what I did, and my keyboard appears to be correct

---

### Post by Stormx on 2006-06-13
I ended up using the irish keyboard layout. Seems to work a treat.

---

### Post by Stormx on 2006-06-13
OOOH! ok! I see! :D

---

### Post by Qtek on 2007-03-01
i have been  looking for that answer for two days,  thank you ! :)

---

### Post by cdyson37 on 2007-03-03
Thanks for that! It's nice to see I'm not the only one who fell for that...

---

### Post by ph0nph0n on 2008-03-05
I had an error while selecting the uk keyboard (something related to kbd, don't remember the exact message), thus some keys weren't working as expected (no pound sign, windows/super key not working...).

I found the solution in a post in ubuntu forums ([British keyboard doesn't work]("http://ubuntuforums.org/showthread.php?t=145108#5")). However the only thing i did is change my xorg.conf and swap the "XkbLayout" value from "uk" to "gb" in the screen input device section.

It now looks like that:
```

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "gb"
EndSection

```

After logging in and out, i get a confirmation message and that was it.

---

