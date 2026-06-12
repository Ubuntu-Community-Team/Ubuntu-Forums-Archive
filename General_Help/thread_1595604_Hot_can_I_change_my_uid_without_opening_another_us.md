---
title: "Hot can I change my uid without opening another user?"
date: 2010-10-13
forum: General Help
---

### Post by davidbr on 2010-10-13
I tried both usermod as su and System->Administration->Users and Groups but I keep getting an error saying the user is logged in (which is true).

so what am I supposed to do? I don't want to open another user just for that...

---

### Post by gsgleason on 2010-10-13
sudo usermod -u nnn username

---

### Post by davidbr on 2010-10-13
```
dave@mypc:~$ sudo usermod -u 875 dave
[sudo] password for dave: 
usermod: user dave is currently logged in
```

---

