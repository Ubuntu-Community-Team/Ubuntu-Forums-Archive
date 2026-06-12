---
title: "kjournald...what is it?"
date: 2009-08-22
forum: General Help
---

### Post by ubudog on 2009-08-22
Anyone know?  Thanks. :)

---

### Post by sandyd on 2009-08-22
thats the journaling service for your ext3 partition.

---

### Post by ubudog on 2009-08-22
Ok. Thanks for the reply, but I mean like what does it do?

---

### Post by jacksaff on 2009-08-22
It logs changes to the hard-drive making your data much more resilient to sudden crashes or power loss. Corrupted data can be automatically restored from the journal.
It's what makes ext3 a much better file system than ext2 in a similar way that ntfs on windows is much better than fat32.

---

### Post by ubudog on 2009-08-23
> **jacksaff said:**
> It logs changes to the hard-drive making your data much more resilient to sudden crashes or power loss. Corrupted data can be automatically restored from the journal.
It's what makes ext3 a much better file system than ext2 in a similar way that ntfs on windows is much better than fat32.

Ah, thanks for the help. :)

---

### Post by ubudog on 2009-08-23
If I were to lose data, how would I go about restoring it with kjournald?

---

