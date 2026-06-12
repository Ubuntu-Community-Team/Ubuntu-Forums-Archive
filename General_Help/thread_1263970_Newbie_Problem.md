---
title: "Newbie Problem"
date: 2009-09-11
forum: General Help
---

### Post by gbuddy66 on 2009-09-11
Hi, newbie here.  I'm running Intrepid 8.10. I 'm realy liking the ubuntu experience. This morning I was reading threads and through terminal did a download that helps with java, MP3 and such.  Now I'm getting this error.E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.\\.  Thank you.

---

### Post by NoaHall on 2009-09-11
Open a terminal (apps -> Accessories -> Terminal) and then run "sudo dpkg --configure -a" and then try again.

---

### Post by Soul-Sing on 2009-09-11
```
sudo dpkg --configure -a
```

in the terminal

---

### Post by P4man on 2009-09-11
well, Id hazard a guess that dpkg was interrupted, so you must manually run 'dpkg --configure -a' to correct the problem :)

But you must do so with root (admin) rights so put sudo in front of it:

```
sudo dpkg --configure -a
```

If it gives any error messages, copy paste them here.

edit: wow, i reply within 1 minute, and Im still beaten by two others lol

---

### Post by gbuddy66 on 2009-09-11
Thank you for the quick responses.  Problem fixed.

---

