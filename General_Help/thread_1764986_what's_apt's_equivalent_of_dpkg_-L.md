---
title: "what's apt's equivalent of dpkg -L?"
date: 2011-05-22
forum: General Help
---

### Post by flyingsliverfin on 2011-05-22
Does apt have an equivalent of dpkg -L?

---

### Post by lithopsian on 2011-05-22
You mean apt-get?  Or aptitude?  apt is the generic name for several tools such as apt-get, apt-cache, etc.

Anyway, I don't think there is a command to produce the exact same output as dpkg -l, but apt-cache pkgnames might do enough for you.

---

