---
title: "Never mount USB Device"
date: 2010-10-14
forum: General Help
---

### Post by Quarkrad on 2010-10-14
Apologies - this is 'out there' but I cannot find it.  I have a USB digital camera that is mounted when connected and switched on.  How can I configure Ubuntu 10.04 so that when ever this device is connected and switched on it is not mounted?

---

### Post by Quarkrad on 2010-10-14
$ gconf-editor

apps > nautilus > preferences
Uncheck the "media_automount" option

---

