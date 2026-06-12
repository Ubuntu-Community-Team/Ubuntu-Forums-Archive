---
title: "How to silence Software Center for an unwanted upgrade?"
date: 2010-04-18
forum: General Help
---

### Post by HiSiskin on 2010-04-18
These days, every morning I boot my PC up, Ubuntu Software Center 1.0.3 says "upgrade your Firefox browser to the version 3.5."  However, the current version of my Firefox is 3.6.3 which has been upgraded via the software's automatic self-update.

I'd like to silence the Ubuntu Software Center for the Firefox upgrade. How to do that?  :confused:

Thanks in advance.

---

### Post by howefield on 2010-04-18
Have you tried locking the package version that you don't want to upgrade via Synaptic Package Manager (Synaptic Package Manager > Package menu > Lock Version).

---

### Post by huygens on 2010-04-18
You maybe have 2 versions of Firefox installed in parallel. You're using the 3.6 by default, but there is an update for the 3.5 as well. It won't harm your installation to make the upgrade. But if I were you and if you do not use the other version, then I would go to the System->Adminstration menu, choose Synpatic, look for firefox-3.5 and uninstall it.

---

### Post by lovinglinux on 2010-04-18
> **HiSiskin said:**
> However, the current version of my Firefox is 3.6.3 which has been upgraded via the software's automatic self-update.

I don't like that method of upgrading, unless you are using a version downloaded directly from Mozilla and running in parallel with the default Firefox version.

It seems, to me, although this is the first I read about such problem, that the package manager is trying to downgrade because you have enable Firefox self-updates. So it checks the version and determine that it is always different, so it keeps prompting for a downgrade.

I would recommend reverting back to Firefox 3.5, disabling Firefox self-update and upgrading it using Ubuntuzilla (32bit) or downloading it from Mozilla. You could also use a PPA to upgrade. See the [[COLOR="Sienna"]**Installing Other Versions**[/COLOR]](http://lovinglinux.megabyet.net/?page_id=220#Installing-Other-Versions-1) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by HiSiskin on 2010-04-18
Thank you all for all of your kind and rapid replies. I'll lock the Ubuntu-controlled version of Firefox by using the Synaptic software. Thanks again.

---

