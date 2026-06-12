---
title: "Mysterious Floppy Drive"
date: 2010-04-28
forum: General Help
---

### Post by wanzeo on 2010-04-28
Hello, I am brand new to ubuntu and I noticed a floppy drive is showing up, and I have no floppy on my computer. Is this normal or is my computer imagining things?

---

### Post by bigsmitty64 on 2010-04-28
Go to places/computer/filesystem/etc folder. Then look for a file called "fstab"
open it and find the line that says:


```
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0        0
```

and change it to this:

```
# /dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0        0
```

you can just copy and paste it from here if you like. That fixed the problem for me! 
:)  good luck,
Smitty

---

### Post by bigsmitty64 on 2010-04-28
Just realized you may have to do this as root. If so, then go to  applications/accesseries and open terminal

and put this in
```
gksudo nautilus
```
hit enter, then your password, a new window will pop up, from within that window, go to the aforementioned file and do what I said in the first post  all your doing is adding a "#" at the beginning followed by a space.

---

