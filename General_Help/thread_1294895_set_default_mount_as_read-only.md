---
title: "set default mount as read-only"
date: 2009-10-18
forum: General Help
---

### Post by mb1shop on 2009-10-18
is it possible to set the default mounts as read-only (or not mount at all)?  i.e. if you insert a new hdd or usb drive, ubuntu will (1) not mount it at all or (2) mount it as read-only

Thanks

---

### Post by Tamlynmac on 2009-10-18
To cancel media auto mount:

system tools/configuration editor/nautilus/preferences

Uncheck "media_automount".

By doing this your system will not mount any inserted media. Including, DVD, CD, sticks, etc.

---

### Post by mb1shop on 2009-10-19
will this work for runlevel 3 also?  I thought mounting was controlled via automount (or similar).

Also... any idea how to get that setting added to a liveCD?  gconf-2?

---

