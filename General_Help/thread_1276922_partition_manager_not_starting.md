---
title: "partition manager not starting"
date: 2009-09-27
forum: General Help
---

### Post by saias on 2009-09-27
hi

i am a new user and i have a small problem.

i am using ubuntu and i am also trying to install winxp. I tried to open partition manage in order to create a fat32 partition but partition manager is not opening. any ideas to fix partition manager or to use another program for the partitioning?

thanks in advance.

---

### Post by drs305 on 2009-09-27
How are you trying to open it?

From Ubuntu or the liveCD Desktop: System, Administration, Partition Editor (or GParted in Karmic).

From the command line, make sure you run it as root:
```

gksu gparted
```
You can also be more specific if necessary, designating the drive:  gksu gparted /dev/sda
If it doesn't open, post the error messages.

---

### Post by saias on 2009-09-27
trying from system administartion partition editor.

tried the command and the error i get is:

 gksu gparted /dev/sda
No protocol specified
(gpartedbin:6873): Gtk-WARNING **: cannot open display: :0.0

---

