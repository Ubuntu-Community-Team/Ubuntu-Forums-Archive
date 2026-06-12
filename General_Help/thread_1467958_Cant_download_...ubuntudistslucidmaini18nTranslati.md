---
title: "Cant download ...ubuntu/dists/lucid/main/i18n/Translation-de.bz2"
date: 2010-05-01
forum: General Help
---

### Post by johnnymenmonic on 2010-05-01
Hi,

when I try to upgrade or update my system I get always the error that there couldnt be downloaded the package ...ubuntu/dists/lucid/main/i18n/Translation-de.bz2. This is obviously a german translation file. How can I solve this problem? This error occurs at every server.

---

### Post by dino99 on 2010-05-01
> **johnnymenmonic said:**
> Hi,

when I try to upgrade or update my system I get always the error that there couldnt be downloaded the package ...ubuntu/dists/lucid/main/i18n/Translation-de.bz2. This is obviously a german translation file. How can I solve this problem? This error occurs at every server.

if you have already switch to other servers, its either a package corruption on your system (can try: sudo apt-get install -f or/and sudo dpkg --configure -a) or a download problem: package corrupted into archive.

---

### Post by johnnymenmonic on 2010-05-01
Sudo apt-get install -f and reconfigure  dont help. How can I repair this corrupted package?

---

