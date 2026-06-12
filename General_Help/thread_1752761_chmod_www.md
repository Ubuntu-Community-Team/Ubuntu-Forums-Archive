---
title: "chmod www"
date: 2011-05-08
forum: General Help
---

### Post by EngMAF on 2011-05-08
i have instaled apachey on my ubuntu
the www folder is under var folde (/var/www)
i am using "chmode 777 -R www/"
but i do that every time i copy files into www
is there is a solution for that ?

---

### Post by Lars Noodén on 2011-05-08
777 is very unsafe.  That last 7 means that *anyone* that can get to that directory can write to it.  Please update it to 775.

The way to avoid having to set the permissions anew each time you upload is to
 
1. change the directory's group to a group you are a member of 
```

sudo chgrp webmasters /var/www

```
2. make the directory group writable
```

sudo chmod g+wr /var/www

```
3. set the sticky bit for the group so that all files will be written as members of that group
```

sudo chmod g+s /var/www

```

---

### Post by EngMAF on 2011-05-09
thanks that solved the problem

---

