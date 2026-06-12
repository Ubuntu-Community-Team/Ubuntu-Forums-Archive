---
title: "Useradd question"
date: 2011-09-13
forum: General Help
---

### Post by saphil on 2011-09-13
Why does the following command give me a user who has no history, tab-completion or regular prompt?

```
sudo useradd exampleuser -m -s /bin/sh -e 20111031
```This one makes a user with more 'normal' parameters

```
sudo useradd exampleuser -m -s /bin/bash -e 20111031
```Is it just because sh points to dash in an Ubuntu system?

---

### Post by dino99 on 2011-09-13
[https://help.ubuntu.com/community/AddUsersHowto](https://help.ubuntu.com/community/AddUsersHowto)

---

### Post by MBybee on 2011-09-13
> **saphil said:**
> Why does the following command give me a user who has no history, tab-completion or regular prompt?

```
sudo useradd exampleuser -m -s /bin/sh -e 20111031
```This one makes a user with more 'normal' parameters

```
sudo useradd exampleuser -m -s /bin/bash -e 20111031
```Is it just because sh points to dash in an Ubuntu system?

Yes. You're more used to bash than sh - sh is not the same shell, any more than csh, ksh, or tcsh are. They have slightly different syntax, rules, and quirks.

On ubuntu 11.04, sh is Dash, bash is still Bash (the Bourne-Again Shell)

---

### Post by haqking on 2011-09-13
> **saphil said:**
> 

Is it just because sh points to dash in an Ubuntu system?


[https://wiki.ubuntu.com/DashAsBinSh](https://wiki.ubuntu.com/DashAsBinSh)

---

