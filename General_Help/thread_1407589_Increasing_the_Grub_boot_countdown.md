---
title: "Increasing the Grub boot countdown"
date: 2010-02-15
forum: General Help
---

### Post by themarker0 on 2010-02-15
You know when you are dualbooting with grub, you have a countdown of 3 seconds? How would i go about to changing that to 30? I have two testing servers using the same monitor and mouse, so i have to log onto those first, if i want to have access to my files. On the server at startup. (I have set up a basic samba server) So thats my crappy reason :P

Any help would be nice. :) Thank you.

---

### Post by s.fox on 2010-02-15
Hello,

Go here: **  /boot/grub/*menu*.*lst***

Locate this line:

```
timeout        3
```

Change it to:

```
timeout        30
```

Hope this helps,

-Silver Fox

---

### Post by themarker0 on 2010-02-15
Thank you so much, silver fox, works like a charm :)

---

