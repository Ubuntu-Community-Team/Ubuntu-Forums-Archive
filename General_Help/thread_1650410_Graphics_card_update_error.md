---
title: "Graphics card update error?"
date: 2010-12-21
forum: General Help
---

### Post by joelkat on 2010-12-21
3D-accelerated proprietary graphics driver for ATI cards.

This driver is required to fully utilise the 3D potential of some ATI graphics cards, as well as provide 2D acceleration of newer cards.

I hit Activate at the bottom and I get SystemError: Failed to lock /var/cache/apt/archives/lock

---

### Post by sikander3786 on 2010-12-21
Means some other package manager like apt-get, Software Center, Update Manager or Synaptic is running. They can't be run simultaneously. Close any other and try again. If you can't see any other running, log out and log back in and it might solve the issue.

---

