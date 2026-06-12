---
title: "Install Oracle, not in /usr"
date: 2010-07-08
forum: General Help
---

### Post by BuggyFunBunny on 2010-07-08
I ran the Oracle .deb, but it didn't give me the chance to specify where to put the files.  I have an SSD for my databases, so /usr/* isn't where I want Oracle.  I was able to run the uninstall, but I've not found a way to specify the directory to drop the files.

Any idea how to do such?

---

### Post by BuggyFunBunny on 2010-07-09
d'oh!!  just install to /usr/lib/oracle, move to the SSD file system and ln back.

---

