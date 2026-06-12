---
title: "Embedded Terminal gedit plugin is missing?"
date: 2009-11-04
forum: General Help
---

### Post by XGhozt on 2009-11-04
I'm on a fresh install of Ubuntu 9.10, and for some reason the Embedded Terminal plugin is missing. Could someone please attach the files here, or link me to where I can download them? I search a bit, but I can't find them anywhere.. :(

Not sure why it would be missing, but I did find a bug report saying that it was missing, and it marked as fixed, but no place for me to download the plugin.

Thanks..

---

### Post by oldos2er on 2009-11-04
[http://live.gnome.org/Gedit/Plugins](http://live.gnome.org/Gedit/Plugins)

---

### Post by XGhozt on 2009-11-04
I don't see it on that page, do you?

Found this picture on google, this is what I'm looking for: [IMG]http://tombuntu.com/wp-content/uploads/2008/05/geditterminal.jpg[/IMG]

---

### Post by oldos2er on 2009-11-04
The embedded terminal is in the package gedit-plugins.
```
sudo apt-get install gedit-plugins
```

---

### Post by mc4man on 2009-11-04
```
sudo apt-get install gedit-plugins
```

should take care of. ( enable the plugin in gedit -> edit -> preferences

---

### Post by XGhozt on 2009-11-06
Thank you, I see all the familiars now. Any idea why these don't come with gedit anymore?

---

### Post by mcduck on 2009-11-06
> **XGhozt said:**
> Thank you, I see all the familiars now. Any idea why these don't come with gedit anymore?

I don't think they ever came with Gedit. I've installed the gedit-plugins package manually in every Ubuntu version.. :)

---

### Post by XGhozt on 2009-11-06
Oh, then I guess I installed them and forgot. :P

---

