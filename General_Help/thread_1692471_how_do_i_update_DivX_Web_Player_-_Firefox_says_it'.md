---
title: "how do i update DivX Web Player? - Firefox says it's vulnerable"
date: 2011-02-21
forum: General Help
---

### Post by nrundy on 2011-02-21
I opened Firefox Add-ons and looked at the Plug-ins. Firefox says the DivX Web Player is in need of a security update. How do I update this? I clicked the button but nothing happens.

---

### Post by Habitual on 2011-02-21
firefox > Tools Menu > Add-ons > Find Updates

---

### Post by nrundy on 2011-02-21
Yes, I tried this. Nothing happens when I click the button for updates.

---

### Post by dvo on 2012-10-01
> **nrundy said:**
> Yes, I tried this. Nothing happens when I click the button for updates.

Indeed, trying the official "check for updates" does not help.
Moreover, on [https://www.mozilla.org/en-US/plugincheck/](https://www.mozilla.org/en-US/plugincheck/) the URI for getting to an update page is missing in the DivX Web Player case.

about:plugins reveals that for Linux this player is in fact Totem: /usr/lib/mozilla/plugins/libtotem-mully-plugin.so
and similarly for the QuickTime Plug-in, VLC Multimedia Plugin, and Windows Media Player Plug-in. 
So the way to update any and all of them appears to be to update totem. 
Yet currently Ubuntu 12.04 LTS still ships version 3.0.1, while [http://ftp.acc.umu.se/pub/GNOME/sources/totem/](http://ftp.acc.umu.se/pub/GNOME/sources/totem/) offers 3.6.

---

### Post by oldos2er on 2012-10-01
Old thread closed.

---

