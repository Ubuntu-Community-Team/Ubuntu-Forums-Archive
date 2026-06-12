---
title: "localhost/test.php not coming up"
date: 2010-03-21
forum: General Help
---

### Post by dayobiz on 2010-03-21
localhost is fine, but localhost/test.php is not coming up. but both programmes has been installed. pls what am i doing wrong?

---

### Post by phen0m on 2010-03-21
what IS coming up?

---

### Post by n0dix on 2010-03-21
I supposed you try with the typical phpinfo() function and works. Check the permissions of the file. Show the test.php file.

---

### Post by sandyd on 2010-03-21
you have to create a file in /var/www/ called test.php. put this in the file. ```
<?php phpinfo() ?>
```

---

### Post by dayobiz on 2010-03-24
thanks mate, localhost is now fine and localhost/test.php too. However php embedded in html files refused to save in /var/www? what is wrong with my server not being able to read .php strings?

---

### Post by n0dix on 2010-03-24
> **dayobiz said:**
> thanks mate, localhost is now fine and localhost/test.php too. However php embedded in html files refused to save in /var/www? 
Perhaps a problem with permissions.

---

