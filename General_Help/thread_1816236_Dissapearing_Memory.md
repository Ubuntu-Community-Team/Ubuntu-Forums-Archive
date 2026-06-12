---
title: "Dissapearing Memory"
date: 2011-08-01
forum: General Help
---

### Post by Orcris on 2011-08-01
I installed Ubuntu with WUBI, and I often seriously damage my Ubuntu and need to reinstall it. Every time I reinstall it, I see that there's about 2 less gigabytes of memory on C:. I never use my Windows partition, so what's happening to my memory?

---

### Post by bcbc on 2011-08-01
Look for a hidden directory C:\FOUND.000 (change drive letter if that's not where you install). I'm willing to bet you'll find some files that windows didn't consider clean and they were 'recovered' for you.

e.g. wubi hides the CD ISO after installing as .fuse_hidden400000... (something like that). I noticed a couple of these on a test drive where I repeatedly installed/uninstalled wubi.

---

### Post by Orcris on 2011-08-02
Thanks. I found that file, and it was taking up the right amount of memory.

---

