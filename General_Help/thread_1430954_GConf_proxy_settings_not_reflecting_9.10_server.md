---
title: "GConf proxy settings not reflecting 9.10 server"
date: 2010-03-16
forum: General Help
---

### Post by sweekar on 2010-03-16
Hi,

I'm running a Ubuntu 9.10 server with Openbox as the WM.
I'm have set the proxy and http_proxy settings at /system/prosy and /system/http_proxy using gconf-editor. 
The settings seem to stick in gconf. The gnome-settings-daemon seems to be running fine. The problem is firefox-3.5, apt etc does not recognize the gconf proxy settings. I do not understand why firefox does not honor these settings.
Is there anything that I'm missing/doing wrong?

Cheers,
Sweekar

---

### Post by sikander3786 on 2010-03-16
For changing proxy setting in Firefox go to

Edit > Preferences > Advanced > Network > Settings

and insert the proxy there.

For apt, open Synaptic Package Manager and go to

Settings > Preferences > Network

and insert the proxy.

I don't think Firefox will follow the GNOME proxy settings however Synaptic should follow. I don't know what is going wrong your case.

The easy way is what I mentioned.

Regards.

Sikander.

---

### Post by dcstar on 2010-03-17
> **sweekar said:**
> Hi,

I'm running a Ubuntu 9.10 server with Openbox as the WM.
.........
I do not understand why firefox does not honour these settings.
........

Firefox no longer uses various Gnome settings after version 3.0.x (like font aliasing).

I believe that it is to make the package more "independent" of the desktop being used, but it is a pain.

I still use FF 3.0.18 because of this, later FF versions look woeful in comparison and you have no choice but to use them in later Ubuntu releases.

---

