---
title: "problem disabling ipv6 in ubuntu 8.08 hardy LTS"
date: 2010-03-26
forum: General Help
---

### Post by fowlerellie on 2010-03-26
hello,can anyone help,i have found the solution to disabling ipv6 but the command line is not recognised when i enter it.

i open terminal and input    sudo gedit/etc/modprobe.d/bad-list/

but the command is not recognised


thanks ellie

---

### Post by Monotoko on 2010-03-26
Hiya Ellie,

I assume you mean Ubuntu 8.04 LTS...as i dont recall an 8.08 ever existing, but the command you want is:

```
sudo gedit /etc/modprobe.d/bad-list/

```

You just forgot the space ^.^

sudo = Execute this command as root, always know what your doing with this.
gedit = Text editing program
/etc/modprobe.d/bad-list/ = The text file your editing with the text editing program

---

