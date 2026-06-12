---
title: "HELP! Ambiance Theme not working!"
date: 2011-01-06
forum: General Help
---

### Post by micael3000 on 2011-01-06
Hello,

I was using ubuntu normaly until yesterday. Today when i turned on my laptop its theme was this way:

[http://img593.imageshack.us/img593/8997/screenshoteg.png](http://img593.imageshack.us/img593/8997/screenshoteg.png)

When i first turn it on, the main panel (where stays "Applications", "Places" and "System") was this color too! But then i just opened System -> Preferences -> Appearance and it self-fixed, without selecting any option, just opening Appearance window.

But the rest of this stuff (like right-click menu and folders) is still messed up!

Does anyone know what is wrong and how to solve it? :/

Thanks in advance!

---

### Post by micael3000 on 2011-01-06
Bump :/

---

### Post by Krytarik on 2011-01-07
It seems to be common bug currently:
[http://ubuntuforums.org/showthread.php?t=1575703](http://ubuntuforums.org/showthread.php?t=1575703)

Try this as a temporary workaround, you may add the command to "System -> Preferences -> Startup Applications"; enter in a terminal:
```
gnome-settings-daemon && killall nautilus
```

---

### Post by micael3000 on 2011-01-07
Today it self-fixed... I did nothing ._.

But thanks for your answer, if it happens again i will try it :P

---

### Post by Krytarik on 2011-01-07
> **micael3000 said:**
> Today it self-fixed... I did nothing .
Again?! This seems to keep happening these days, without any obvious package update related to the issue. :popcorn:
[http://ubuntuforums.org/showthread.php?t=1660675](http://ubuntuforums.org/showthread.php?t=1660675)
[http://ubuntuforums.org/showthread.php?t=1660102](http://ubuntuforums.org/showthread.php?t=1660102)

However, happy that it's fixed!

---

