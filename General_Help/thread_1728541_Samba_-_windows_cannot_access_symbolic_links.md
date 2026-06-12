---
title: "Samba - windows cannot access symbolic links"
date: 2011-04-13
forum: General Help
---

### Post by kooldino on 2011-04-13
I have samba set up, and I can log in, etc.  However, whenever I try to access a symbolic link, windows tells me that "windows cannot access [directory name]".

I have this under global, but it doesn't seem to help:

>  follow symlinks = yes
 wide symlinks = yes
 unix extensions  = no

The permissions of the target directories are open.

Help!

---

### Post by kooldino on 2011-04-14
Bump

---

### Post by Don Barzini on 2011-04-15
This is the syntax...

```

follow symlinks = yes
wide links = yes
unix extensions = no
```

After editing the **smb.conf** file..... You must restart the Samba service.

---

### Post by kooldino on 2011-04-16
That worked, thanks.

---

