---
title: "Linking Commands"
date: 2010-12-26
forum: General Help
---

### Post by isracanman on 2010-12-26
Hi,

A program which I am using requires a fortran compiler to  work, I am using gfortran. However the program works best with version  4.5 of gfortran, which I can install by running 'apt-get install  gfortran-4.5'. However, the program is programmed to run the command  'gfortran' which does not call this version. I can install gfortran as  well by running 'apt-get install gfortran', but I am pretty sure this is  installing an older version (how can I check this by the way?).
Is there a way to tell Ubuntu to treat every call for 'gfortran' as a call for 'gfortran-4.5'?

thanks,
Yev

---

### Post by TeoBigusGeekus on 2010-12-26
You can use an [alias]("http://www.linfo.org/alias.html").

---

### Post by tredegar on 2010-12-26
The following commands
```
which gfortran
ls -l $(which gfortran)
locate gfortran-4.5 | grep bin
ls -l /etc/alternatives | grep fortran
```

will hopefully help you understand how linux sorts out the different versions that are installed, and which is used as the default.

---

### Post by isracanman on 2010-12-26
Thanks a lot!

---

### Post by isracanman on 2010-12-26
> **TeoBigusGeekus said:**
> You can use an [alias]("http://www.linfo.org/alias.html").

Does this make a permanent alias? How to do that?

---

### Post by TeoBigusGeekus on 2010-12-26
It says how in the link.
Put the alias in your ~/.bashrc file.

---

