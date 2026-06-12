---
title: "Root password"
date: 2011-09-19
forum: General Help
---

### Post by Gordenhf on 2011-09-19
Recently installed Ubuntu 11.04. Making good progress but have one question. I set up a "root" user with pw etc but probably did prematurely. How can I revert that action ie remove "root" as a user and simply go back to a 1 user environment. thanks in advance. Gorden

---

### Post by sisco311 on 2011-09-19
Hi, and welcome to the forums!

The following command will lock the root account password:
```
sudo passwd -dl root
```
-d deletes the password hash
-l locks the password

More info here:
[uhelp]community/RootSudo[/uhelp]

---

