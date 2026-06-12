---
title: "Moving files / folders into existing archive"
date: 2009-09-14
forum: General Help
---

### Post by Krews on 2009-09-14
Hi , anybody know a command for moving an existing folder into an existing .tar.bz2 archive ?

---

### Post by SecretCode on 2009-09-14
Take a look at ```
man tar
``` and check the -r/--append option and the -u/--update option. Together with --bzip2 this should allow you to do what you want.

---

