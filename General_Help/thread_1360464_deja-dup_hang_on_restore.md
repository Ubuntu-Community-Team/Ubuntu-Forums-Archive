---
title: "deja-dup hang on restore"
date: 2009-12-20
forum: General Help
---

### Post by truthseer0 on 2009-12-20
i backed up my entire home folder to my external HD and now wish to restore it. when i try deja-dup it seems like it's searching for a second before freezing, and dying on its feet. from running in the terminal, this is all i get:
```
** (deja-dup:2271): DEBUG: DuplicityInstance.vala:138: Running the following duplicity (2288) command: nice ionice -c2 -n7 duplicity collection-status --no-encryption file:///media/FreeAgent Drive --verbosity=9 --volsize=5 --archive-dir=/root/.cache/deja-dup --log-fd=18

```
can anybody help me? thank you.

btw, running 32-bit Karmic before and after

---

### Post by mikix on 2009-12-21
Thanks for the report!  It sounds like you hit a bug.  Please file a bug report against Deja Dup:
[https://bugs.launchpad.net/deja-dup/+filebug](https://bugs.launchpad.net/deja-dup/+filebug)

That form has instructions for how to get more verbose output.

---

