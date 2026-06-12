---
title: "Update manager not updating to latest kernel?"
date: 2009-08-09
forum: General Help
---

### Post by Longines on 2009-08-09
Two laptops both running 9.10.

On both, Update Manager says they are up to date.

Laptop A is running 2.6.28-14. Laptop B is running 2.6.28-15.

A is a 6 year old Celeron 1.8/512MB. Laptop B is 3 year old PentiumM 1.73/2GB.

I'm curious as to why A hasn't been upgraded to 28-15?

TIA.

---

### Post by michy99 on 2009-08-09
Click the button in Update Manager to check for updates.

---

### Post by Longines on 2009-08-09
Done. No change.

---

### Post by michy99 on 2009-08-09
Different repositories, maybe? Compare /etc/apt/sources.list on the two computers.

---

### Post by Longines on 2009-08-10
Thanks. Turns out Laptop B has 'Proposed updates' enabled.

---

