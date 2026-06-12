---
title: "is debsrc needed for upgrade or install packages?"
date: 2006-02-15
forum: General Help
---

### Post by shams2 on 2006-02-15
hi,
i have slow download rate, and apt-get update will vast more time for the deb-src repos , can i desable deb-src repos, and run the apt-get for upgarde and install packages?

---

### Post by nanotube on 2006-02-15
hm, afaik, should not be any problems if you remove the src repos from your list...

---

### Post by deBaas on 2006-02-15
[QUOTE=shams2]hi,
i have slow download rate, and apt-get update will vast more time for the deb-src repos , can i desable deb-src repos, and run the apt-get for upgarde and install packages?[/QUOTE]
Thats no problem, just comment then out in the sources.list file.

---

