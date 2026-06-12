---
title: "starting xbmc before the windows manager"
date: 2011-08-28
forum: General Help
---

### Post by tweakmy on 2011-08-28
Hi there,
I have disable the gdm and have openbox running from .xinitrc

in ~/.xinitrc

[HTML]exec /usr/bin/xbmc &
exec /usr/bin/openbox-session[/HTML]

Everything work out fine, but when i reboot the machine, I can see momentarily of the window manager before xbmc is fully loaded on full screen.

Is there a way to delay the openbox before the xbmc is fully loaded?
and is there a way to check xbmc is already fully loaded except for the wait command?

---

