---
title: "permissions for /var/cache/debconf/passwords.dat"
date: 2012-10-11
forum: General Help
---

### Post by claracc on 2012-10-11
Hello, I have 12.04 gnome fallback, and seeing the .xsessions-errors file I have found this error:

> debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permiso denegado


I went to /var/cache/debconf/passwords.dat file and found the permissions were:

> -rw-------  1 root root       0 jul  6  2009 passwords.dat


Are these permissions  correct?.

As you can see this is an empty file. Can I safely remove?

Thanks in advance.

---

### Post by claracc on 2012-10-14
Bump....

Can I safely remove /var/cache/debconf/passwords.dat?

Someone knowing about filesystem?

---

### Post by conradin on 2012-10-14
everything you want to know, about the file-system hierarchy standard.
[www.pathname.com/fhs/pub/fhs-2.3.pdf](www.pathname.com/fhs/pub/fhs-2.3.pdf)

why do you want to delete it? 
make a backup, and a boot disk and try it. it things fail, boot into the live dusk and replace your coppy with the back up.
Since your file is in a cache, i bet you can delete the entire /var/cache/debconf folder which would probably just make debconf or whatever pkgmanager, not work. Aptitude would probably just rewrite the files for you if you told it to.

Also, yuor permissions look fine.

---

### Post by claracc on 2012-10-15
> **conradin said:**
> everything you want to know, about the file-system hierarchy standard.
[www.pathname.com/fhs/pub/fhs-2.3.pdf](www.pathname.com/fhs/pub/fhs-2.3.pdf)

why do you want to delete it? 
make a backup, and a boot disk and try it. it things fail, boot into the live dusk and replace your coppy with the back up.
Since your file is in a cache, i bet you can delete the entire /var/cache/debconf folder which would probably just make debconf or whatever pkgmanager, not work. Aptitude would probably just rewrite the files for you if you told it to.

Also, yuor permissions look fine.

Thanks for answering.

I am not going to delete it since it can cause problems with debconf.

I asked about the possibility of safely deleting the file since I was warned by .xsessions-errors: 

debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permiso denegado (permission denied).

Also, there is the fact that it is an empty file, so I thought it was unneccessary.

---

### Post by conradin on 2012-10-19
The xsession error permission denied means that the program should have been running in sudo mode. so, whatever command youre using, give the sudo command first.

---

### Post by toddlohenry on 2013-09-15
Thank you, Conradin. This solved the problem for me!

---

