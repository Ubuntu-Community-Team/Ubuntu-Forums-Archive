---
title: "Simply can't boot up"
date: 2011-06-05
forum: General Help
---

### Post by Kolbe on 2011-06-05
Due to complications, the laptop running Ubuntu had a hard reset during the 11.04 update.

Now when I try to turn on the machine, I'm met with:
"The disc drive for / is not ready yet or not present
Continue to wait; or Press S to skip mounting or M for manual recovery"

Anyone with a similar experience or the technical knowledge able to help with this?

---

### Post by mikewhatever on 2011-06-05
It looks like the file system has been corrupted during the hard reset. You'll need to run a check on it from the Live CD. From a terminal window:

```
sudo fsck -y /dev/sdXY
```

where sdXY is your Ubuntu root partition.

---

