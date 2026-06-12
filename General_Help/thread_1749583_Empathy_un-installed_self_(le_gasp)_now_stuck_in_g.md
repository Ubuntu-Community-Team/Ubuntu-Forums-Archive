---
title: "Empathy un-installed self (le gasp) now stuck in gtk3 dependancy hell"
date: 2011-05-04
forum: General Help
---

### Post by Shadowgamon on 2011-05-04
I noticed it was un-installed when I tried to video chat with my girlfriend this afternoon. but Empathy was nowhere to be found! when I went into the terminal (apt-get install ) it spit up this ```
empathy : Depends: libchamplain-0.10-0 (>= 0.9.0) but it is not installable
           Depends: libchamplain-gtk-0.10-0 (>= 0.9.0) but it is not installable
           Depends: libgck0 (>= 2.92.92.is.2.91.1) but it is not installable
           Depends: libgcr-3-0 (>= 2.92.92.is.2.91.4) but it is not installable
           Depends: libgnome-control-center1 (>= 1:2.91.2) but it is not installable
           Recommends: nautilus-sendto-empathy but it is not going to be installed
           Recommends: freedesktop-sound-theme but it is not installable
E: Broken packages

```This is not something I expected from the guys at canonical. Default programs breaking!:(

---

### Post by Shadowgamon on 2011-05-05
Bumping before it falls too deep in here

---

