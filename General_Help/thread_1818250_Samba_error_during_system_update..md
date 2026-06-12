---
title: "Samba error during system update."
date: 2011-08-04
forum: General Help
---

### Post by Excquis on 2011-08-04
Setting up samba4 (4.0.0~alpha15~git20110124.dfsg1-2ubuntu1) ...
/var/lib/dpkg/info/samba4.postinst: 45: /usr/share/samba/setup/upgradeprovision: not found
dpkg: error processing samba4 (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 samba4
E: Sub-process /usr/bin/dpkg returned an error code (1)

I've tried removing it from /usr/bin...tried deleting every vestige of samba on my system. Even when I attempted to sudu apt-get remove samba, the same error showed up.

Can anyone help me with completely removing samba so that I do not have those annoying error messages every update?

---

### Post by Excquis on 2011-08-05
Fixed. After doing some additional research I found the command sudo apt-get autoremove and clean, hurray!

---

