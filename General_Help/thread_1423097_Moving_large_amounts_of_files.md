---
title: "Moving large amounts of files"
date: 2010-03-06
forum: General Help
---

### Post by dbrine on 2010-03-06
I am trying to move a large amount of files (over 30k and 86GB) to another HDD but I get a Augment list too large error?? I tried rsync, cp, mv and still the same error

---

### Post by PeEllAvaj on 2010-03-06
Can you post what command you are trying to run?  "Argument list too long" typically means you are using a wildcard (which expands to the entire list of files as a feature of the shell), when you should be passing a recursive flag to rsync/cp/etc.

---

