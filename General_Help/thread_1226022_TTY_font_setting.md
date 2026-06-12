---
title: "TTY font setting"
date: 2009-07-29
forum: General Help
---

### Post by hoagie on 2009-07-29
Hello fellow users,
I am trying to change the default font of tty in ubuntu server. I don't use a graphical environment so having a font that is easily readable is important. In arch there is a setting in rc.conf for fonts, I know that ubuntu doesn't have an rc.conf, but I can't find a config file for fonts.
Thanks in advance.

---

### Post by Zorael on 2009-07-29
You can change fonts and font size (to an extent) by reconfiguring console-setup. Installing *some* package unlocks Terminus fonts which look much nicer, but I've yet to figure out which. Driveby readers are welcome to fill in the blanks.
```
$ sudo dpkg-reconfigure console-setup
```

---

### Post by hoagie on 2009-07-29
Well thanks that did the trick. Terminus was unlocked by default I didn't have to install anything. I acually use TerminusBoldVGA and it looks nice.
If I install other fonts will they also appear in the setup to choose or do I have to move them to a specific directory or something?

---

