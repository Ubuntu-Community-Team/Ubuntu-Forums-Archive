---
title: "Chromium -&gt; Missing Plug-In"
date: 2012-01-03
forum: General Help
---

### Post by xeroxed_yeti on 2012-01-03
Hi together,

I've got trouble with chromium (15.0 on Ubuntu 11.10).

Everything works great but using any add on with IE Tab functionality (e.g. IE Tab; IE Tab Classic; IE Tab Multi) ends up with an error message:

'Missing PlugIn'

However using such an addon will allow me to use our company's Microsoft Outlook Web Application (OWA) in full modus, not in lite. Because those addons allows to run ActiveX controls.

Flash, java, etc works fine using the normal chromium tabs - starting a new tab with IE Tab functionality ends up with the error message. Disabling/Enabling plugins listed in about://plugins did not help.

How can I check which kind of plugin is missing in Chromium - starting chromium in the shell with chromium-webbrowser didn't not work :-/

Has anybody run in this error message and find the solution?

Thanks,
Yeti

---

### Post by vasa1 on 2012-01-03
IMO, the IE Tab add-on requires access to a functional Internet Explorer engine (Trident), something that is not present in Ubuntu 11.10 or any Linux system *per se*. I don't know whether you'll have better luck after installing Wine.

---

### Post by Stanley_00 on 2012-01-03
If you have firefox installed, you can give it a try.

---

### Post by xeroxed_yeti on 2012-01-03
Thanks for your help vasa,
Wine works fine - wine + the corresponding dev packages are installed

Thanks for your help Stanley,
Since the last updates of firefox I'm really disappointed in firefox, it becomes very slow and uses a huge amount of RAM in comparison to chromium. I have to admit that "my" firefox is full of addons, but disabling those addons results in that firefox still uses much more RAM than chromium (...chromium 50MB - firefox  ~250MB).
However the the webaccess works in the "full" version.

---

