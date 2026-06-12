---
title: "do I need the directiory /var/cache/apt/archives?"
date: 2010-05-23
forum: General Help
---

### Post by puzzler995 on 2010-05-23
My /var/cache/apt/archives directory has almost 9000 items and is over 12 GB big. All it contains is a bunch of .deb files. Do I need this file or can I delete it to save hard drive space?
Thanks,
Puzzler995

---

### Post by oldos2er on 2010-05-23
```
sudo apt-get clean
``` will clear your apt cache. /var/cache/apt/archives contains *deb packages of software you've installed.

---

### Post by puzzler995 on 2010-05-23
Thanks man, that worked :)

---

