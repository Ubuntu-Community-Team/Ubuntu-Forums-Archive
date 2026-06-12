---
title: "Live cd root password"
date: 2010-06-23
forum: General Help
---

### Post by bth73 on 2010-06-23
Is there a password for root log in? 
I can't copy and move files to other hard drives from the live cd.
I've searched for 45min now and find nothing

---

### Post by surfer on 2010-06-23
open a shell and

```
$ sudo -s
```

you will be asked for a password, leave it empty and hit enter.

in order to copy files, you will have to mount your disk (to [FONT="Courier New"]/mnt[/FONT] e.g).

---

### Post by snowpine on 2010-06-23
Press Alt+F2 and type:

```
gksu nautilus
```

---

### Post by bth73 on 2010-06-24
thanks, hope it works, getting in/out errors when I try to move folders, but I can move individual, or groups of files.

---

