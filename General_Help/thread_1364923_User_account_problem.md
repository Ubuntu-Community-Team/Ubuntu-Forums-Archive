---
title: "User account problem"
date: 2009-12-26
forum: General Help
---

### Post by nitishsuvarna on 2009-12-26
I have more than 1 user account on my ubuntu 9.10 system.I want to delete 2 of them.How it is done.I tried throgh admin-user $ grup but it wasnt deleting completly.

---

### Post by The Secret on 2009-12-26
```
sudo userdel -r [COLOR=DimGray]<username>[/COLOR]

```

What you mean by saying that *it wasnt deleting completly* ?

---

### Post by nitishsuvarna on 2009-12-26
sorry but i want to say that it was deleting in  admin-user & group but not in
log in menu.TNX

---

### Post by chuina on 2009-12-26
By reading your thread, i've just tried this.
And you are correct , everything is not deleting from the Admin>user&groups menu.

the "user's home folder" remains in the > /home folder

I delete the "user's home folders" manually from > /home/

Also i need to edit /etc/passwd and /etc/group

(Be caution to delete anything)

---

### Post by Leppie on 2009-12-26
you can use deluser to delete the account + home folder:
```
$sudo deluser --remove-home <username>
```

or use the -r option:
```
$sudo userdel -r <username>
```

---

