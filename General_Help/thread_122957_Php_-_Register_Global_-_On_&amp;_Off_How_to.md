---
title: "Php - Register Global - On &amp; Off How to ?"
date: 2006-01-28
forum: General Help
---

### Post by sharif_aly on 2006-01-28
Register Global in Php how to set to on and off ?

---

### Post by TheForumTroll on 2006-01-29
Edit your php config. It should be in there somewhere ;) 

But it should be off by default. Do you want it on? I wouldn't recommend that as its very easy to get unsecure code that way.

---

### Post by gruepig on 2006-01-29
The default in php these days is off (0). Running php with register_globals is tremendously insecure.  That said, php configuration options, including register_globals, are set in the file /etc/php4/apache2/php.ini (assuming apache2 and php4; the path is similar for other versions).

If you are going to turn register_globals on, make sure you understand the implications first.  Searching for "register_globals" on [http://www.php.net](http://www.php.net) is a good start.

---

