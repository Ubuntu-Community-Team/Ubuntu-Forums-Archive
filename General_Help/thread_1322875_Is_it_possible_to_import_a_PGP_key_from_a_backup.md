---
title: "Is it possible to import a PGP key from a backup?"
date: 2009-11-11
forum: General Help
---

### Post by NFblaze on 2009-11-11
So apparently, I didnt export my keys from my previous install. It may be on backup but, I dont know the path for where to look for it in the backup. Does anyone know if I can find these keys? Thanks

---

### Post by Commander_Keen on 2009-11-11
You may have to do a complete restore for you to do an export.
if you can use Virtual Box
Create a virutal session.
Restore.
Export.

---

### Post by mr_steve on 2009-11-11
> **NFblaze said:**
> So apparently, I didnt export my keys from my previous install. It may be on backup but, I dont know the path for where to look for it in the backup. Does anyone know if I can find these keys? Thanks

Your keys should be in ~/.gnupg. You need the pubring.gpg and secring.gpg files which are your public and private keyrings, respectively.

I believe the commands to re-import are something like:
```
gpg --import pubring.gpg
gpg --import secring.gpg
```

---

### Post by NFblaze on 2009-11-11
I went with the latter approach , and the keys did import successfully. Thanks for you guys help.

---

