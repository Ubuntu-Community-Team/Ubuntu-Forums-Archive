---
title: "how to undo recent updates?"
date: 2011-10-18
forum: General Help
---

### Post by liquidmonkey on 2011-10-18
i just did an update and my system is a bit messed up with regards to some libusb which was working fine yesterday.

how can i undo the most recent update that i did in 11.10?


any help here is greatly appreciated.

---

### Post by Bmonsterboy on 2011-10-18
I don't think so, but you could try finding older versions of the package/s that you want reverted.

---

### Post by liquidmonkey on 2011-10-18
does ubuntu not take a 'snapshot' or 'restore point' before each update?

---

### Post by mcduck on 2011-10-18
> **liquidmonkey said:**
> does ubuntu not take a 'snapshot' or 'restore point' before each update?

No, it doesn't. Although you are free to set up such backup features yourself, 11.10 even comes with a built-in tool for the purpose.

Anyway, you can use th Synaptic Package Manager to force installation of a previous version of a certain package. (you'll have to install Synaptic first, if you haven't done that already). Just select a package, and the from the menu Package->Force Version. You'll also find the option to lock the package to a certain version in the same menu.

Of course the old version of the package needs to be available somewhere so you can install it... (If it's not available in any of the repositories you are using, you could check in /var/cache/apt/archives in case the old .deb package is still there.)

Anyway, if you do that keep in mind that it is likely to cause problems with future updates. So you definitely should also file a bug report about the problem and monitor updates on that so you'll be able to unlock the package version again at some point and get back to using the up-to-date versions from Ubuntu's repositories.

---

