---
title: "Programs"
date: 2010-01-14
forum: General Help
---

### Post by okmijn22 on 2010-01-14
Where are programs installed in Ubunutu. For exmaple if I want to access, where can I access it from without the shortcut.

---

### Post by MelDJ on 2010-01-14
hi. take a look at this [http://raviratlami1.blogspot.com/2007/01/how-to-know-directory-folder-of-linux.html](http://raviratlami1.blogspot.com/2007/01/how-to-know-directory-folder-of-linux.html)

---

### Post by okmijn22 on 2010-01-15
I typed whereis 7zip but nothing showed up.

---

### Post by marshmallow1304 on 2010-01-15
> **okmijn22 said:**
> I typed whereis 7zip but nothing showed up.

Do you have p7zip installed?  It provides two executables: 7zr and p7zip.

---

### Post by okmijn22 on 2010-01-16
I see it thank you. So infront of every program you must add a letter `p`

---

### Post by konqueror7 on 2010-01-16
usually you will find them in the */sbin* folder for system programs, and */bin* folder for other programs,,,there is also the */usr* which where your applications are, and there is also */opt* in which other applications use instead...

you may want to try out the 'whereis' command to find where a specific application is located...```
whereis firefox
```

---

### Post by MelDJ on 2010-01-16
> **okmijn22 said:**
> I see it thank you. So infront of every program you must add a letter `p`

no. because the programs name is p7zip hence the p is put in front

---

