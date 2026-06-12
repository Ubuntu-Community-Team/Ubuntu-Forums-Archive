---
title: "Upgrade to 9.10"
date: 2010-01-12
forum: General Help
---

### Post by D.M. on 2010-01-12
What is the command to start 9.10 upgrade from Terminal?

---

### Post by prshah on 2010-01-12
> **D.M. said:**
> What is the command to start 9.10 upgrade from Terminal?

If you have the "alternate" CD, then use the command```
sudo /media/cdrom/cdromupgrade.sh
``` If you want to upgrade across the Internet, and have a working Internet connection, please use```
sudo update-manager --dist-upgrade
``` To upgrade to Lucid now, you need to use ```
sudo update-manager -d
``` to enable upgrading to a "development" release.

---

### Post by slakkie on 2010-01-12
See the link in my signature.

---

