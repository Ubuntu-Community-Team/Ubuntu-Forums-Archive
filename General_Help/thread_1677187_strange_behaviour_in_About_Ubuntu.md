---
title: "strange behaviour in About Ubuntu"
date: 2011-01-28
forum: General Help
---

### Post by Tectuktitlay on 2011-01-28
Hi all,

Something weird is happening in my ubuntu installation. I installed Maverick (10.10), but when I open *About Ubuntu* in the System menu of Gnome it happily reports:

> You are using Ubuntu 11.04 - the Natty Narwhal - released in April 2011 and supported until October 2012.

I got nervous and checked my /etc/apt/sources.list, but I clearly lists only Maverick repositories.

Does anyone know what's going on?

Grtz,

Tec

---

### Post by Rubi1200 on 2011-01-28
Hi,
this is a bug:
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/690248](https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/690248)

From the terminal:

```
cat /etc/*release
```

This will show you the correct information.

---

### Post by Tectuktitlay on 2011-01-28
Thanx Rubi1200!

---

### Post by Rubi1200 on 2011-01-28
No problem, you are more than welcome :-)

---

