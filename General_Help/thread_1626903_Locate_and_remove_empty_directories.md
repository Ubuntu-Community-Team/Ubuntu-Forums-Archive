---
title: "Locate and remove empty directories"
date: 2010-11-20
forum: General Help
---

### Post by Cool Javelin on 2010-11-20
After using fdupes, I find I have lots of empty directories now, Is there any utility to automatically locate and remove them?

NO GUI, I am using a text only server (10.04.)

Thanks, Mark.

---

### Post by fearphage on 2010-12-02
This is the command I used:

```
find . -depth -empty -exec rmdir '{}' \;
```

It deletes all empty subdirectories of the current folder.

---

### Post by Spyderkid on 2010-12-02
You can download BleachBit from the repositories which cleans up your computer

---

### Post by Cool Javelin on 2010-12-02
Thank you Spyderkid & fearphage for the answers,  will try both ideas.

I see someone is a Voyager fan. Seven of Nine rocks.

Mark

---

