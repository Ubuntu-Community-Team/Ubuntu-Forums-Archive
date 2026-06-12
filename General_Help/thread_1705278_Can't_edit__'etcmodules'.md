---
title: "Can't edit  '/etc/modules'"
date: 2011-03-12
forum: General Help
---

### Post by Zinthos on 2011-03-12
I need to edit a file but it won't let me. I thought I figured out the right. I tried:
```
sudo chmod -R 777 /etc/modules
```But that doesn't work I get this error message:

```
sudo: must be setuid root
```Neither does this:

```
gksudo gedit /etc/modules
```How do I go about doing this the right way? Thanks in advance for any help.

---

### Post by vivek.pandey on 2011-03-12
have you tried using sudo vi /etc/modules?

---

