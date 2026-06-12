---
title: "Packages being held back"
date: 2010-05-09
forum: General Help
---

### Post by wrose51106 on 2010-05-09
On a fresh install of Ubuntu 10.04, from the cli I run apt-get update then apt-get upgrade. I get 3 packages being held back:

linux-generic-pae
linux-headers-generic-pae
linux-image-generic-pae

Can anyone shed some light onto this, thanks!

-Bill

---

### Post by MooPi on 2010-05-09
This is a normal situation and nothing to worry about. Linux kernel is being kept back because the necesary packages to satisfy linux-generic have not yet been added to the repositories. Or your system uses a specific kernel.

---

### Post by jerrrys on 2010-05-09
the pae kernel is the server kernel.  so unless your running more than 4 gig of ram, you probably don't have a use for it

---

### Post by gmargo on 2010-05-09
"apt-get upgrade" is protecting you by not upgrading in certain cases.

Use "apt-get **dist-**upgrade" (or "aptitude **full-**upgrade") to get the full upgrade experience. Be sure to reboot after the kernel upgrade.

Read the **apt-get** (or **aptitude**) man page for a full explanation of the difference.

---

