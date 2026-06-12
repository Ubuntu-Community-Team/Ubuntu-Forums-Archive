---
title: "problem with chmod"
date: 2009-06-28
forum: General Help
---

### Post by Therax on 2009-06-28
hi

i used chmod to give me write access to /etc/sudoers
but now i cant restore it or run any sudo commands all i get is
sudo: /etc/sudoers is mode 0777, should be 0440

any help with how to fix this thanks

---

### Post by Brandon Williams on 2009-06-28
Reboot into single-user (a.k.a. recovery) mode and use chmod to change the permissions back to 440.

---

### Post by Therax on 2009-06-28
okay will do thanks

---

### Post by michy99 on 2009-06-28
You are supposed to use visudo to edit the sudoers file. Did you make a backup first?

---

### Post by Therax on 2009-06-29
okay no but its working now.

---

