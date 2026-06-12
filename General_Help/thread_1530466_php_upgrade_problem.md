---
title: "php upgrade problem"
date: 2010-07-13
forum: General Help
---

### Post by mickey13 on 2010-07-13
I'm trying to upgrade php5 from 5.2.4 to 5.2.13 [on Ubuntu 8.04.4 LTS].  I've downloaded the source, did ./configure (tried some different switches), make, make install (as sudo).  Seems like the installation went fine (no errors).  But here's my problem:

**> php -v**
php5.2.13

**> php5 -v**
php5.2.4

Seems like there are 2 installations of php.  I think the server admin before me may have done a lamp-server install.  I've restarted apache2, but the php.info page still shows the old version (5.2.4).  After looking at some apache2 config files it looks like the /usr/lib/apache2/modules/libphp5.so wasn't updated (and I think that's the problem).  The 5.2.13 installation process didn't seem to generate the libphp5.so  Any ideas?

---

### Post by mickey13 on 2010-07-14
Since lamp-server was probably installed and could account for 1 of the 2 php installations, is there a way to update just the php portion of LAMP to a specific version number?

---

### Post by mickey13 on 2010-07-14
I think if I can generate the libphp5.so from the php5.2.13 build, I can replace the one being referenced by apache2.  Does anyone know the proper ./configure switches in order to get the shared object generated?  I've tried several different ones with no luck.  I'm surprised that on what seems to be a successful install, that the library isn't generated.  Thanks.

---

### Post by mickey13 on 2010-07-14
Is there a way to configure apache2 to use a specific installation php?

---

