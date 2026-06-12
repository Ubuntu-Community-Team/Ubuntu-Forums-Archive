---
title: "please help with respitory"
date: 2006-03-04
forum: General Help
---

### Post by souteneur3190 on 2006-03-04
how do i enable all respitorys only if i have access to a shell, is this possible?  Im trying to help my firend, when i try to aptget something thats not restricted its  ok, but he need to un restrict it in a  terminal.

---

### Post by souteneur3190 on 2006-03-04
all were trying to do is download this:

sudo apt-get install xorg-driver-fglrx

but i think its restricted

---

### Post by Ramses de Norre on 2006-03-04
do ```
sudo vi /etc/apt/sources.list
```
in terminal and uncomment all the lines starting with "deb" to enable universe and multiverse.

EDIT: type 'i' to go to insert mode so you can change lines, then ESC, shift+q, type wq!

---

### Post by souteneur3190 on 2006-03-04
do i need to update

---

### Post by Ramses de Norre on 2006-03-04
Yes, you always need to run sudo apt-get update when you changed your repo's.

---

