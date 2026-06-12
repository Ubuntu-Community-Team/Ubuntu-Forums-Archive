---
title: "Ubuntu is running in low-graphics mode"
date: 2009-12-12
forum: General Help
---

### Post by pigimon on 2009-12-12
Ubuntu flashes after the shiny ubuntu circle at the middle and says

Ubuntu is running in low-graphics mode

Your screen,graphics card,and input device settings could not e detected correctly. You will need to configure these yourself.
ok button

heres how this happened.. ubuntu updates and i try to connect my new logitech dinovo desktop laser (combined keyboard and mouse wireless) and before i restart for the update (don't remember if it needed it but i think it did because it was a big one) i tried to install blues (plus Dbus lib cause i didn't have it) and i messed a bit with it,tried to do some stuff.the keyboard and mouse was working tho but not with all its functions (extra keys etc)


so i install blueZ and then i restart my pc and i get this message,then got my old usb keyboard and mouse cause the new one didn't work...

so now i can't click or move or press enter but as i was reading some similar threads i found out about dpkg-reconfigure xserver...(not the whole command) and i booted through recovery mode and i typed that command. then i rebooted and the same stuff again.... so please if you have any ideas would be sooo helpful i have so many files that i don't want to lose.....thanks in advance.

---

### Post by YosefKaro on 2009-12-12
I am just starting to get the same message that you got about running in low-graphics mode after rebooting and the computer running fsck.  This is the first time that this has happened to me and I have not added any new hardware or anything else: I am on a laptop.  Please, any suggestions.

-Yos

---

### Post by YosefKaro on 2009-12-12
> **pigimon said:**
> Ubuntu flashes after the shiny ubuntu circle at the middle and says

Ubuntu is running in low-graphics mode

Your screen,graphics card,and input device settings could not e detected correctly. You will need to configure these yourself.
ok button

This is exactly what I am seeing after todays updates.

-Yos

---

### Post by pigimon on 2009-12-12
so anything new like any answers or posts like that or nothing ?  im still stuck not able to find any solutions about this please if you find it say it to me too... thanks a lot..

---

### Post by YosefKaro on 2009-12-13
](*,)](*,)](*,)](*,)

---

### Post by drz4007 on 2009-12-13
if you can load the os even on low graphics mode, why dont you reinstall the apropriate driver for your gpu once more? i usually do this after some upgrades when i have the same problem.

---

### Post by pigimon on 2009-12-13
ok i'd like help for dat i guess :$

---

### Post by YosefKaro on 2009-12-13
pigimon,

This is now a confirmed bug on launchpad.  You can subscribe to it [here]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/495973")

-Yos

---

### Post by pigimon on 2009-12-13
oh thanks a lot mate

---

### Post by mercury00 on 2010-02-18
Was there any solution to this issue?

---

