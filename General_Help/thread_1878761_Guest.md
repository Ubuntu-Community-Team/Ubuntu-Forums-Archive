---
title: "Guest"
date: 2011-11-10
forum: General Help
---

### Post by The Legend Mohammad on 2011-11-10
how to disable guest session in ubuntu 11.10 ?

---

### Post by proxx1850 on 2011-11-10
Users & groups ?

I dont have a guest account by default, just me ?

---

### Post by The Legend Mohammad on 2011-11-10
I didn't fond it in Users & groups guest account is active on my computer

---

### Post by Elfy on 2011-11-10
Hi - backup and edit lightdm.conf

```
sudo cp /etc/lightdm/lightdm.conf /etc/lightdm/lightdm.conf.bak
gksudo gedit /etc/lightdm/lightdm.conf
```

Add this to the end of the file 

```
allow-guest=false
```

Save and close - should be gone on the next login

---

### Post by The Legend Mohammad on 2011-11-12
thank you
but I can't save the file
the file is read only

---

### Post by Elfy on 2011-11-13
When you ran the first command did it ask for password? Did the same happen with the second command?

If you tried to edit the file without gksudo then try it with.

---

### Post by The Legend Mohammad on 2011-11-13
:lolflag:

thank you very much

---

### Post by Elfy on 2011-11-13
Assuming the thanks is for it all working as wanted now can you make thread solved please - I could do it - but I'd mauch rather you did ...

And you are welcome :)

---

