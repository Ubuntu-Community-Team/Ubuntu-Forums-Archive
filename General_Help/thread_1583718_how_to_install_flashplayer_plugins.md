---
title: "how to install flashplayer plugins?"
date: 2010-09-28
forum: General Help
---

### Post by warakawa on 2010-09-28
so I downloaded this tar.gz file off adobe site, extracted it which turn into a .so file. Now what do I do.

---

### Post by gandaran on 2010-09-28
> **warakawa said:**
> so I downloaded this tar.gz file off adobe site, extracted it which turn into a .so file. Now what do I do.
put the libflashplayer.so file in the browser plugins folder but look this is not the recommended way to install flash because this flash wont get updated.
to install flash install it from the system repositories either from software center, synaptic package manager or apt-get
using apt-get, copy and paste to terminal
```
sudo apt-get install flashplugin-installer
```

---

### Post by dirty_harry on 2010-09-28
I recommand flash-aid:
[https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

But as gandaran said, installing it the Ubuntu-way enables automatic updates an so on...

---

