---
title: "chmod on /var/"
date: 2010-12-23
forum: General Help
---

### Post by gabe17 on 2010-12-23
Hi!

I've accidentally run chmod -R 777 on my /var/ directory (but stopped, so only some files were made chmod 777). I want to ask if it's "dangerous" in any way and if it could have something caused. I would be also very thankful if you told me how to "get it back". (which chmod is original in this directory)

Thanks.

---

### Post by karthick87 on 2010-12-23
Type the following,
```
chmod -R 644 /var/
``` 
```
chmod -R a+X /var/
```
```
chmod -R 777 /var/tmp /var/lock
```

---

### Post by gabe17 on 2010-12-23
Thanks a lot!

---

### Post by gabe17 on 2010-12-23
Sorry, one more question...now my MySQL database doesn't work. ```
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (13)
```

---

