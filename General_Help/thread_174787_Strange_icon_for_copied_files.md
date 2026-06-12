---
title: "Strange icon for copied files?"
date: 2006-05-12
forum: General Help
---

### Post by Zdravko on 2006-05-12
After copying some files from NTFS partitions into home under Ubuntu, I noticed that every file and directory has a "lock" picture over its icon in Nautilus. What does this mean? How can I remove this?

---

### Post by Omnios on 2006-05-12
That deals with permitions, you might want to try changing the permitions either by right clicking it / properties / permitions or doing a chmod if it owned by root.

---

### Post by cgjones on 2006-05-12
I believe this means the files are owned by some other user, probably root, and you don't have write permissions on them. You should be able to change this by typing the following command in the terminal.
```

sudo chown -R *yourusername*:*yourgroup* *lockeddirectory/*

```

---

### Post by Zdravko on 2006-05-12
Thanks.

---

