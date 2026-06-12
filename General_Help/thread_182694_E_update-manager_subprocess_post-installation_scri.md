---
title: "E: update-manager: subprocess post-installation script returned error exit status 134"
date: 2006-05-26
forum: General Help
---

### Post by Jeandré on 2006-05-26
Opened update manager, checked for updates, downloaded and installed an update for update manager, got error.

Setting up update-manager (0.42.2ubuntu12~breezy2) ...
*** glibc detected *** corrupted double-linked list: 0x0804c9f0 ***
/var/lib/dpkg/info/update-manager.postinst: line 6:  8280 Aborted
 scrollkeeper-update -q >/dev/null 2>&1
dpkg: error processing update-manager (--configure):
 subprocess post-installation script returned error exit status 134
Errors were encountered while processing:
 update-manager
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

