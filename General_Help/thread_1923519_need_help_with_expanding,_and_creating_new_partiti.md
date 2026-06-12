---
title: "need help with expanding, and creating new partitions with gparted"
date: 2012-02-10
forum: General Help
---

### Post by Marko90 on 2012-02-10
i have 50 gigs of unalocated space, and i want to expand my 12 gig
filesystem partition using  gparted.

i also created one 50gig partition (ext2) but every time i try create folder on it, or do anything else, it would not allow me.

there is a folder inside named "lost and found" that when i try to access, it says; "Folder contents cannot be displayed", "You do not have necessary permission to view lost+found".

---

### Post by Vishnu V on 2012-02-10
Hi
Try this to remove the access permission problems
open a terminal
```

sudo su
chown username path_to_the_drive

```

---

### Post by forrestcupp on 2012-02-10
As for expanding your filesystem partition, it won't let you change a partition that is mounted. You'll have to boot to a LiveCD or USB install and make sure to not mount that partition before you can change it with GParted. If that doesn't work, your best bet is to use the GParted Live CD.

---

### Post by jerrrys on 2012-02-11
[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

---

