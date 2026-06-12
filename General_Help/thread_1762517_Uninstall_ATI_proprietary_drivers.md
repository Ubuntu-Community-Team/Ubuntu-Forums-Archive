---
title: "Uninstall ATI proprietary drivers"
date: 2011-05-19
forum: General Help
---

### Post by uShafee on 2011-05-19
I downloaded and installed drivers from [http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx) instead of using Jockey. How do i uninstall the ati drivers?

---

### Post by cottfcfan on 2011-05-19
```
sh /usr/share/ati/amd-uninstall.sh
```
```
sh ati-driver-installer-x86.x86_64.run --uninstall
```
One of those commands should work.
You may have to prefix them with sudo.

---

### Post by uShafee on 2011-05-19
thanks :) it worked with the uninstall option

---

