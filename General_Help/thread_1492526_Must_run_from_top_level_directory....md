---
title: "Must run from top level directory..."
date: 2010-05-24
forum: General Help
---

### Post by duckwars on 2010-05-24
For some reason when I try to go through this walkthorugh
[http://martinml.com/en/linux-on-asus-eeepc-1005p/](http://martinml.com/en/linux-on-asus-eeepc-1005p/)

on the 4th step
"./scripts/driver-select ath9k"


I get an error after which is
"Must run ./driver-select from the compat-wireless top level directory"

Any ideas?  Thanks.

---

### Post by happyhamster on 2010-05-24
Is there a file called "compat-release" in the compat-wireless-... folder? (If not, try putting an empty text file with that name in that folder.)

---

### Post by duckwars on 2010-05-25
> **happyhamster said:**
> Is there a file called "compat-release" in the compat-wireless-... folder? (If not, try putting an empty text file with that name in that folder.)

This worked! Thanks!

---

