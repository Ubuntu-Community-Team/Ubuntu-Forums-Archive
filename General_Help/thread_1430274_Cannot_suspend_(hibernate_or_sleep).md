---
title: "Cannot suspend (hibernate or sleep)"
date: 2010-03-15
forum: General Help
---

### Post by TheNessus on 2010-03-15
kubuntu 9.10, KDE 4.4.1, Nvidia driver 195

jeff@jeff-lappy:~$ sudo hibernate
hibernate:Warning: Tuxonice binary signature file not found.
Some modules failed to unload: nvidia
hibernate: Aborting suspend due to errors in ModulesUnloadBlacklist (use --force to override).

I even installed this tuxonice thing but to no avail...

---

### Post by TheNessus on 2010-03-15
hmmm..

---

### Post by TheNessus on 2010-03-15
ok, so after rebooting it works just fine. Installing that missing program solved it. I guess it simply got removed during upgrading to 4.4.1?

---

