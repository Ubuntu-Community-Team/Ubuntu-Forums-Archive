---
title: "Unofficial purged package still appears in synaptic"
date: 2010-06-11
forum: General Help
---

### Post by rolandpish on 2010-06-11
Hi!

I added a third-party repository and installed a package (that is not in the official repos).
After some minutes I decided to uninstall the package (apt-get remove package), remove the repository and execute apt-get update.
All went without problems.
But if I open synaptic the uninstalled package is still listed as an available package. If I right-click it->properties->versions shows the already removed repository.

If I execute apt-cache search package, no results are shown, but synaptic stills lists it.

How can I remove the package from synaptic?

Thanks in advance

---

### Post by rolandpish on 2010-06-11
Sorry for the noise.
It was in the "residual config" group so I needed to purge it.

---

