---
title: "PHP Startup: Unable to load dynamic library"
date: 2011-07-23
forum: General Help
---

### Post by mbeltoft on 2011-07-23
I keep getting mails with this warning on my 11.04 server

```

 PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20090626/mysql.so' -
 /usr/lib/php5/20090626/mysql.so: cannot open shared object file: 
No such file or directory in Unknown on line 0

```

apparently everything is working as it should and I don't know how to get rid of this warning

---

### Post by mbeltoft on 2011-07-23
I think it figured it out..

i needed to install php5-mysql

---

