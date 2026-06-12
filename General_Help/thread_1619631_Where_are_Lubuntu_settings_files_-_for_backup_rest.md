---
title: "Where are Lubuntu settings files? - for backup restore and transfer"
date: 2010-11-12
forum: General Help
---

### Post by DJonsson2008 on 2010-11-12
I'd like to move my Lubuntu desktop/menu/wallpaper 
settings to another computer, where are these settings stored?

I would of course backup/restore my entire home folder but I need discrete access to Lubuntu settings only, as am moving to a machine
with a different Ubuntu installation/configuration and just want to
transfer my Lubuntu desktop and menu to the other machine.

---

### Post by bioterror on 2010-11-12
Ou righty then!

```
scp -r .config/ lubuntu-user@new-lubuntu:.
```

and this becouse there's few directories and easier to move whole .config ;)

You get your chromium-settings too.

---

### Post by DJonsson2008 on 2010-11-12
Thanks now digging .config directory
can see several lxde...* folders will
simply backingup/restoring these have
the same effect?

---

### Post by bioterror on 2010-11-12
I would just install openssh-server on the new machine, and use that scp to move .config

But sure you can do it like that too.

---

