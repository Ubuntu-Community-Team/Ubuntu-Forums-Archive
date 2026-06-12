---
title: "How do I change permissions on root folders and files"
date: 2010-06-14
forum: General Help
---

### Post by Jonners59 on 2010-06-14
I need to change the config in a folder and can not due to it being owned by root.  How do I change the permissions.

Folder = /etc/stunnel/
file = /etc/stunnel/stunnel.conf

---

### Post by velle frak on 2010-06-14
Would opening the file with sudo do the trick?

e.g. sudo vi /etc/stunnel.stunnel.conf

---

### Post by julio_cortez on 2010-06-14
> **Jonners59 said:**
> How do I change the permissions.
Have you already tried running **chmod** as root (with **sudo**, of course)?

**EDIT:** never mind, try velle frak's method before..
It will spare you another **sudo chmod** after having modified the file ;)

---

### Post by blchinezu on 2010-06-14
you don't have to change its permissions.. you can simply edit the file with sudo

```
sudo gedit /etc/stunnel/stunnel.conf     
```

---

### Post by Jonners59 on 2010-06-14
> **blchinezu said:**
> you don't have to change its permissions.. you can simply edit the file with sudo

```
sudo gedit /etc/stunnel/stunnel.conf     
```

Excellent, worked perfectly!!!!

To velle frak and julio_cortez
Thanks guys...
:lolflag:

---

