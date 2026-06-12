---
title: "Disable login screen sound."
date: 2010-02-06
forum: General Help
---

### Post by &#999;&#978;&#625;&#595;&#9786;l on 2010-02-06
I'd like to disable the log-in **screen** sound. Not after you log on.
Since it's my laptop I can't just switch a knob or press the off button.
The function keys don't work before log-in.. Well not for sound at least.. I guess you could say it's a bug.. unless it was intended.

Anyway, without filling a bug report how can I disable sound @ the login screen?

Thanks in advance.

---

### Post by wojox on 2010-02-06
Run in a terminal:

```
sudo -u gdm gconftool-2 --set /desktop/gnome/sound/event_sounds --type bool false
```

That will get rid of the drum sound.

---

### Post by dcstar on 2010-02-06
> **&#999 said:**
> I'd like to disable the log-in **screen** sound. Not after you log on.
Since it's my laptop I can't just switch a knob or press the off button.
The function keys don't work before log-in.. Well not for sound at least.. I guess you could say it's a bug.. unless it was intended.

Anyway, without filling a bug report how can I disable sound @ the login screen?

Thanks in advance.

[http://ubuntuforums.org/showpost.php?p=8672597&postcount=17](http://ubuntuforums.org/showpost.php?p=8672597&postcount=17)
[http://nuclear-imaging.info/site_content/2009/11/03/remove-karmic-ubuntu-910-login-screen-sound/](http://nuclear-imaging.info/site_content/2009/11/03/remove-karmic-ubuntu-910-login-screen-sound/)

---

