---
title: "Directory"
date: 2009-09-25
forum: General Help
---

### Post by bobevt on 2009-09-25
I have no idea how to get to the root directory I used cd /root said I was unauthorized
I need to run dpkg-reconfigure because my fan stays on.ubuntu 9.04 Toshiba Satellite L350
 
Thank you for your help

---

### Post by zvacet on 2009-09-25
You have to run command with sudo like this

```
sudo dpkg-reconfigure your_command
```

---

### Post by mthalis on 2009-09-25
> sudo -i

after that 

> cd /root

---

### Post by davec64 on 2009-09-25
Hi,

to get to root you just need to type in a terminal:

```
cd /
```

If you then type:

```
ls
```

It will list whats there.

However if you need to run dpkg-reconfigure i don't think you need to go to the root directory to run it (I might be wrong!)

---

### Post by bobevt on 2009-09-25
Thank you all! I'll keep trying.

---

