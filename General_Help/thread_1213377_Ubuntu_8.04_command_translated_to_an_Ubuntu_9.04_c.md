---
title: "Ubuntu 8.04 command translated to an Ubuntu 9.04 command?"
date: 2009-07-14
forum: General Help
---

### Post by bastion on 2009-07-14
[B]apparently im supposed to do this command in Ubuntu 8.04 but I need it to work in Ubuntu 9.04 which it isn't. should i write it differently?

```
sudo ../../b43-fwcutter-011/b43-fwcutter -w /lib/firmware wl_apsta_mimo.o
```[/B]

---

### Post by ptn107 on 2009-07-14
Install Ubuntu's b43-fwcutter package (not the one from linuxwireless.org):

```
sudo aptitude install b43-fwcutter
```

Answer 'yes' if it asks you to fetch and install firmware.  Then your done.  You won't need that command.

---

### Post by TheCrap on 2009-07-14
[LEFT]on the projectpage is written: "This driver was included into the [Linux kernel]("http://www.kernel.org/") since 2.6.17-rc2." Ubuntu 9.04 has Kernel 2.6.28 so i think its no longer necessary.
[/LEFT]

---

