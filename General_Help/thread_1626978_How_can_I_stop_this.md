---
title: "How can I stop this?"
date: 2010-11-20
forum: General Help
---

### Post by DjLoveMonkey on 2010-11-20
Please Help.

This dialogue keeps appearing,  Could not find "/media/SimpleDrive_/ehh/db" . It then force opens a window looking for the file. 

Thanks

---

### Post by MooPi on 2010-11-20
Details please. What were you doing and what applications do you have open ?

---

### Post by DjLoveMonkey on 2010-11-20
I had tried to access a .flv file in the folder it did not play. The folder then locked up and asked for a force quit then this problem occurred.

---

### Post by MooPi on 2010-11-20
What app were using to play the file ?

---

### Post by DjLoveMonkey on 2010-11-20
Movie player

---

### Post by MooPi on 2010-11-20
Open a terminal and type
```
killall -e totem
```
That should kill the movie player from searching.

---

### Post by DjLoveMonkey on 2010-11-20
It is still looking for the folder.

---

### Post by MooPi on 2010-11-20
Can you open the system monitor and see if something is spiking a cpu heavily, under processes. Or you can just log out then back in ?

---

