---
title: "Can't load mysql extension in PHP"
date: 2011-02-20
forum: General Help
---

### Post by alzorz on 2011-02-20
I installed LAMP according to these instructions [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)
whit sudo taksel install lamp-server

I've moved the mysql(i).so files to /usr/lib/php5/ext/

and added these lines in the php.ini file

extension=mysql.so
extension=mysqli.so
extension_dir="/usr/lib/php5/ext/"

But it still wont load, what am i doing wrong?

---

### Post by wojox on 2011-02-20
That's kind of an old post. I've never had to move that module for Apache to load it. Did you restart Apache?

---

### Post by alzorz on 2011-02-20
I've restarted it loads of times using, sudo service apache2 restart

---

### Post by Habitual on 2011-02-20
```
sudo apt-get install php5-mysql
```

---

### Post by alzorz on 2011-02-20
> **Habitual said:**
> ```
sudo apt-get install php5-mysql
```

It's already installed, should i remove and install again?

---

### Post by Habitual on 2011-02-20
That shouldn't be necessary but it wouldn't hurt to try.

---

### Post by wojox on 2011-02-21
I would undo what you did and try again. The page clearly states it's for 6.06 and lower.

---

