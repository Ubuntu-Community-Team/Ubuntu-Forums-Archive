---
title: "Firefox Launch Error *Please Help*"
date: 2011-12-19
forum: General Help
---

### Post by JF382 on 2011-12-19
Has anyone else ever gotten this error? Happens every time I launch Firefox on Ubuntu. Please help. Thanks. I will appreciate ANY answers.

---

### Post by Jdogzz on 2011-12-19
Have you tried removing Firefox and reinstalling it? Your installation may have become corrupted.

---

### Post by JF382 on 2011-12-19
> **Jdogzz said:**
> Have you tried removing Firefox and reinstalling it? Your installation may have become corrupted.


Yes i did it does the same thing after reinstalling

---

### Post by JF382 on 2011-12-19
it only happens when i launch from the unity sidebar. if i launch in a folder no problem. dosent make sense...

---

### Post by lovinglinux on 2011-12-20
Close Firefox, then delete the file *cert8.db* from your profile, located under **~/.mozilla/firefox/<profilename>/cert8.db**. If that doesn't help and if you are sure the .mozilla folder has the correct permissions and your drive is not full, then try to create a new profile with the profile manager:

```
firefox -P
```

---

