---
title: "wierd problem sofware center (PLEASE HELP!!!) i can't do anything"
date: 2011-02-26
forum: General Help
---

### Post by bullets_hurt on 2011-02-26
i wante to reinstall the gnome panel hoping it would reinstall looking just like it did when i first installed ubuntu (shutdown wifi all of that junk)

so i uninstalled it and then for some dub reason closed the software center dumb right, because now there is no way to open ubuntu software center

ps
i only just got ubuntu a couple of days ago and don't know much of anything about it, oh and its 10.10 if it matters

PLEASE HELP

---

### Post by Matt__ on 2011-02-26
alt + F2

then type in ```
gksudo synaptic
```

install what you need from there

---

### Post by bullets_hurt on 2011-02-26
that doesn't do anything for me like nothing is happening but i found the th ubuntu software center in  the filesystem menu can you or someone tell me what the default panel would be called so i can install it again

sorry if i'm dumb

---

### Post by Matt__ on 2011-02-26
so alt+F2 dosnt work?

---

### Post by bullets_hurt on 2011-02-26
it never has for me, what does it do.

---

### Post by Matt__ on 2011-02-26
its standard behaviour for Ubuntu.
hold alt and press F2 brings up the "run application" box.

or try ctrl + F2

all we need is to get either synaptic or a terminal running..can you get either of those up?

---

### Post by bullets_hurt on 2011-02-26
nope does nothing, um, do you know what the default panel is called i'm trying to find it in software center, but i forget the name.

thanks for being helpful btw

---

### Post by Matt__ on 2011-02-26
gnome-panel as far as i recall...im on a very customized 10.10 atm, no panels at all :)

---

### Post by Matt__ on 2011-02-26
or just reinstall ubuntu-desktop from software center

---

### Post by bullets_hurt on 2011-02-26
i found it and now that it's installed again alt+f2 works but it doesn't have default settings will re-installing ubuntu desktop fix that

---

### Post by bullets_hurt on 2011-02-26
nevermind i got it fixed

---

### Post by Frogs Hair on 2011-02-26
If you have a working panel you can restore defaults by running this code.
```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```

---

