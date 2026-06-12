---
title: "not updating somethings over ssh."
date: 2010-04-29
forum: General Help
---

### Post by Name141 on 2010-04-29
Hello, why is it some upgrades are held back when installing over ssh or simply in the terminal with "sudo apt-get update && sudo apt-get upgrade" ?

Such as today The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic


I have to turn it's monitor on , login to the machine through the GUI, and then run update manager for it to install them.

Would I be able to set something for it to update it without me having to login to the GUI ? or is this the only way to upgrade such packages properly?

---

### Post by gmargo on 2010-04-29
"apt-get upgrade" (and "aptitude safe-upgrade") will not upgrade certain packages if it involves removing other packages.  Use "apt-get dist-upgrade" (or "aptitude full-upgrade") to get the complete upgrade.  See the man pages for apt-get and aptitude for full details.

---

### Post by Name141 on 2010-04-29
> **gmargo said:**
> "apt-get upgrade" (and "aptitude safe-upgrade") will not upgrade certain packages if it involves removing other packages.  Use "apt-get dist-upgrade" (or "aptitude full-upgrade") to get the complete upgrade.  See the man pages for apt-get and aptitude for full details.

So I really need to be using 'dist-upgrade' ?

---

