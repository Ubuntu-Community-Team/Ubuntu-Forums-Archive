---
title: "creating xorg.conf"
date: 2009-10-28
forum: General Help
---

### Post by Wim Sturkenboom on 2009-10-28
Somebody posted a reply in some thread here that described how to generate an xorg.conf file for the Buntu's that don't have one. [COLOR="Blue"]I'm trying to find that thread or the command that will actually generate a xorg.conf.[/COLOR]

I don't need this for myself at this stage (I still have 8.04 with a fully populated xorg.conf) and I can probably create one from scratch if I have to using the trial-and-error method.
But one can not advise an inexperienced user that wants to try Linux to go through those hassles.

---

### Post by falconindy on 2009-10-28
```
dpkg-reconfigure -phigh xserver-xorg
```
The above will backup (if existing) and recreate your /etc/X11/xorg.conf file.

---

### Post by Wim Sturkenboom on 2009-10-28
Thanks. Can't remember it was that (easy) one, but will give it a shot / advise if necessary.

---

