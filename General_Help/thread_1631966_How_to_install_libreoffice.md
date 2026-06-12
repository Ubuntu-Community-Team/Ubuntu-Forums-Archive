---
title: "How to install libreoffice???"
date: 2010-11-27
forum: General Help
---

### Post by maghoxfr on 2010-11-27
I just downloaded libreoffice beta, but can't install it. I know I suck but how do I do it? Because I downloaded what I thought to be a .deb package but I really can't find the way to install it.

Help?

---

### Post by azertyh on 2010-11-27
hello,
if it's a .deb file, double-click installs it.
and in tips and tutorials forum, there is a thread about how to install libreoffice.

---

### Post by maghoxfr on 2010-11-27
double clicking on it opens more folders. I'll check the tips and tutorials thanks.

---

### Post by maghoxfr on 2010-11-27
Followed that tutorial and I'm using libreoffice now. Thanks.

---

### Post by georgemc on 2010-11-27
from the LibO mailing list, download the tar.gz file, then:

```

cd <directory containing the tar.gz file>
tar xzvf <tar.gz file>
cd LibO_3<tab> [or fill in the complete name manually]
cd DEBS
sudo dpkg -i *.deb
cd desktop<tab>
sudo dpkg -i *.deb

```hope this helps.

George

---

