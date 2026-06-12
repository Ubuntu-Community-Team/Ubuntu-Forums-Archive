---
title: "how to run make distclean"
date: 2011-07-04
forum: General Help
---

### Post by nizsu on 2011-07-04
Hi guys, 
I'm totally new. As the title says, how to run make distclean

---

### Post by mc4man on 2011-07-04
> **nizsu said:**
> Hi guys, 
I'm totally new. As the title says, how to run make distclean

Why?

(used to clean  configured or compiled source files

---

### Post by nizsu on 2011-07-09
Im trying to install a program into my computer. I use terminal n receive this message "Source firectory is already configured. please run make distclean there first?"

---

### Post by matt_symes on 2011-07-09
Hi

Navigate to the folder containing the make file and type (in the terminal)

```
make distclean
```What is the program you are trying to install ? It may be in the repositories so you may not have to build it.

You have installed build-essential ?

```
sudo apt-get install build-essential
```Kind regards

---

