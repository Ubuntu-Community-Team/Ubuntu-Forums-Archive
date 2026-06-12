---
title: "cd /home/$user   does not work"
date: 2011-03-30
forum: General Help
---

### Post by bobeyuno on 2011-03-30
I'm trying to set up a minecraft server and all the files are in my user area.
If I type:

jack@ubuntu:/home$ cd /jack
bash: cd: /jack: No such file or directory

it recognises cd /home

I don't understand how else it is wrong, please help

---

### Post by TBABill on 2011-03-30
```
cd jack
```

---

### Post by bowens44 on 2011-03-30
> **bobeyuno said:**
> I'm trying to set up a minecraft server and all the files are in my user area.
If I type:

jack@ubuntu:/home$ cd /jack
bash: cd: /jack: No such file or directory

it recognises cd /home

I don't understand how else it is wrong, please help

once in /home just do a cd jack

---

### Post by bobeyuno on 2011-03-30
That works thanks guys :D

---

### Post by garvinrick4 on 2011-03-30
OP already has it figured out.

---

### Post by supershin on 2011-03-30
your home folder full path is /home/jack so enter:
cd /home/jack

or a shortcut is ~/

---

