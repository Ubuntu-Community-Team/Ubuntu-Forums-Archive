---
title: "Cannot remove user and it's home directory"
date: 2009-08-30
forum: General Help
---

### Post by masraha on 2009-08-30
I have a problem to remove one user and it's directory
i've use rm -rf *(the directoriy), it's not work.
also the user cannot remove by using "users and group" menu.

help me please.


thanks in advance

---

### Post by Liolikas on 2009-08-30
sudo rmuser -r name

---

### Post by credobyte on 2009-08-30
```
sudo rm -r /home/username

```

Regarding [COLOR=RoyalBlue]Users and groups[/COLOR] dialog - did you [COLOR=RoyalBlue]unlocked[/COLOR] it ?

---

### Post by twosev on 2009-08-30
I suppose you should have a super-user (root) privileges. Try to make this command:
```
sudo userdel -rf <login>
```
Good luck.

---

### Post by masraha on 2009-08-30
> **Liolikas said:**
> sudo rmuser -r name

the result
```
sudo: rmuser: command not found
```> **credobyte said:**
> ```
sudo rm -r /home/username

```Regarding Users and groups dialog - did you unlocked it ?
i did unlock it, then i deleted it, but when i open Users and groups dialog again, those user still in the user list.

---

### Post by Liolikas on 2009-08-30
try userdel

---

