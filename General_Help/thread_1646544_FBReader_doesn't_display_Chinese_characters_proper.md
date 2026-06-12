---
title: "FBReader doesn't display Chinese characters properly."
date: 2010-12-16
forum: General Help
---

### Post by asdf1 on 2010-12-16
On Linux Mint FBReader (both the latest version and the one in the 10.04 repositories)displays Chinese characters as boxes(see screenshot) for some reason, but on Windows it works fine. Is there any way to fix it?

---

### Post by asdf1 on 2010-12-19
I managed to fix it. FBReader has a config.xml file in /usr/share/FBReader/default which specifies the font used in the program. I changed the font and the Chinese characters displayed fine.

---

