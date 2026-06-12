---
title: "Unlinking files."
date: 2009-11-26
forum: General Help
---

### Post by oxygen on 2009-11-26
Hi,

I've got some linked files (soft and hard) which I want to unlink. I don't want to delete the file I just want to make the files in each folder non-linked.

Obviously I can manually do:

```

unlink /path/to/file/b
cp /path/to/file/a /path/to/file/b
```

But would prefer a single command. Any ideas?

---

### Post by PeEllAvaj on 2009-11-26
From my understanding (I would prefer someone else chime in), hard links are all equal pointers to a space on disk.  This means that you can delete either the link you made, or the original and the remaining will continue to work, and simply be a pointer to the disk.

Soft links don't work like this, you will have to run the 2 commands.

---

