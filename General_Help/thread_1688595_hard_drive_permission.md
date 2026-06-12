---
title: "hard drive permission"
date: 2011-02-15
forum: General Help
---

### Post by piano_man9009 on 2011-02-15
I've got three hard drives from broken computers and a laptop, i need the files off at least two of them.  They mount fine, but i can't access a lot of the files on the disks as i do not have the permissions necessary.  How to i access these files?  I'm running off a usb live disk.

---

### Post by kn0w-b1nary on 2011-02-15
try typing this in terminal:
```
gksu nautilus
```

then browse to the files you need.

Hope this helps!

---

### Post by rafaelks on 2011-02-15
Look your permissions here:
> ls -l /media
And put this if you don't have permissions:
> chmod 777 /media/(disco)

---

### Post by kn0w-b1nary on 2011-02-15
you could also add after "ls -l" ```
chown your_username filename
``` when you're as root.

---

