---
title: "Phtml"
date: 2010-02-22
forum: General Help
---

### Post by daniel50096230 on 2010-02-22
Hi, I tried to open PHP page in my Ubuntu 9.04 Firefox, but it prompt out a box ask me to open or save file. The box look like this:

You have chosen to open

which is a :application/x-httpd-php
from:[http://localhost](http://localhost)

What should Firefox do with this file...


Can anyone tell me what wrong with it?? I am running Ubuntu 9.04, Apache2 and Php 5 and GNOME Desktop 2.26.1.


I had cleared Firefox cache, but the problem still haven resolved yet.

---

### Post by mörgæs on 2010-02-23
Did you boot the machine after installing the servers?

---

### Post by daniel50096230 on 2010-02-23
Yes, i did.

---

### Post by mörgæs on 2010-02-23
What happens if you save

```
<?PHP
phpinfo();
?>
```as test.php and call [http://localhost/test.php](http://localhost/test.php) ?

---

