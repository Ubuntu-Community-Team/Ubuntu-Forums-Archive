---
title: "Problems when installing new ethernet adapter"
date: 2009-08-25
forum: General Help
---

### Post by Rinman on 2009-08-25
I've been trying to replace my onboard ethernet adapter with a new one (PCI, D-Link DFE-530TX). When I have then both installed and activated the new one works fine. However, since the onboard adapter no longer works and some systems, like mysql, seems to default to the first eth adapter I want to disable it and only use the new one. Problem is that when I do that the new one doesn't work at all.

I guess there are some settings from the old eth0 that is incompatible with the new adapter, but how do i change them? Is there a tool for this or do I have to change things manually?

Thanks
Rinman

---

### Post by HermanAB on 2009-08-25
Howdy,

You can re-assign the ethernet device names in /etc/udev/rules.d/61-net_config.rules

---

### Post by Rinman on 2009-08-25
Thanks, I think that worked!

Didn't know eth adapters kept their designation even after you had disabled/diconnected them.

Cheers
Rinman

---

