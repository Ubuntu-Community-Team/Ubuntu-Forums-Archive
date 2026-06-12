---
title: "Changing ownership of a file/directory"
date: 2012-04-04
forum: General Help
---

### Post by zac2290 on 2012-04-04
My macbook died on me and im trying to recover the files. Its connected to a USB enclosure and is located /media/Macintosh HD/Users/Zac

It is telling me I don't have permissions to read the files.

I tried using:

sudo chown zac /media/Macintosh HD/Users/Zac

but it comes back with:

chown: cannot access '/media/Macintosh': No such file or directory
chown: cannot access 'HD/Users/Zac': No such file or directory

The space is seeming to cause it to fail. All I want is to recover my files! Please help!

---

### Post by brainwash on 2012-04-04
Simply use quotes to avoid problems with spaces:
```
sudo chown zac "/media/Macintosh HD/Users/Zac"
```

---

### Post by zac2290 on 2012-04-04
Thank you for the reply,

That worked, but it changed the owner from "root" to "501 - user #501" instead of my account "zac"

Thoughts?

EDIT:
Actually I'm not even sure its working - when I run the command I get this
chown: changing ownership of `/media/Macintosh HD/Users/zac': Read-only file system

I still can't access the folder and it ls -l shows it is owned by 501 in the dialout group


Any help is appreciated!!

---

