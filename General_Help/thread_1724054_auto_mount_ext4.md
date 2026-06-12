---
title: "auto mount ext4"
date: 2011-04-07
forum: General Help
---

### Post by ELD on 2011-04-07
What would you say is the easiest way to auto mount an ext4 partition on my hard drive?

---

### Post by pqwoerituytrueiwoq on 2011-04-07
using the /etc/fstab file
also see man fstab

```
UUID=YOUR-UUID-HERE /media/storage           ext4    defaults
```

---

### Post by ELD on 2011-04-07
Doesn't give me write support mate.

---

### Post by pqwoerituytrueiwoq on 2011-04-07
i am sure someone around here knows the correct permissions numbers
this is the line i use for windows
UUID=CC00D9ED00D9DE90 /mnt/windows ntfs defaults 0 2
and i need to check it for anything i want to keep before i scrap it when i build my rig next week
you will probably find something searching the forums for fstab

---

