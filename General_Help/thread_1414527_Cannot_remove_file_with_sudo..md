---
title: "Cannot remove file with sudo."
date: 2010-02-23
forum: General Help
---

### Post by thatsdaniel on 2010-02-23
Hi!
I have this nasty file that eats away my very soul, since I can not remove it.
When I try the following I get this output:

```
sudo rm -rf 1
rm: cannot remove directory `1': Directory not empty
``````
ls *
ls: cannot access the filename ½.png: No such file or directory
``````
ls -al
ls: cannot access the filename ½.png: No such file or directory
total 16
drwxrwxr-x  2 thatsdaniel 1003 12288 2010-02-23 20:19 .
drwxrwxr-x 18 thatsdaniel 1003  4096 2010-02-23 20:26 ..
-?????????  ? ?      ?        ?                ? the filename ½.png
``` Oh right, I unmounted the disc an fsck'ed it and output reported clean.

Ideas, please? :D

---

### Post by gmargo on 2010-02-23
Did you force fsck to run (with the **-f** option) or did it return quickly and say the filesystem was clean?  If the latter, then try the former.

---

### Post by thatsdaniel on 2010-02-23
Yepp, that solved it. Thanks! :D

---

### Post by Iowan on 2010-02-24
I noticed that you changed the title of your first post to [SOLVED]. You can mark the thread [SOLVED] by clicking on the option under Thread Tools.

---

