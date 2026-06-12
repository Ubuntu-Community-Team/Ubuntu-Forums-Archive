---
title: "PHP - open in firefox: localhost...?"
date: 2012-01-09
forum: General Help
---

### Post by dmsherrill on 2012-01-09
I'm running Ubuntu 11.04 and have LAMP installed. I store my PHP files at.... var/www/php 
When I open a file with Firefox, it will open like this... file:///var/www/PHP/test.php  -- (which does not work). 

If I change the address to... localhost/PHP/test.php
It will render the PHP code just fine. Is there a way to tell the files in var/www to open starting with localhost/?

I'm pretty new to this so any help will be appreciated. Mark

---

### Post by mcduck on 2012-01-10
> **dmsherrill said:**
> I'm running Ubuntu 11.04 and have LAMP installed. I store my PHP files at.... var/www/php 
When I open a file with Firefox, it will open like this... file:///var/www/PHP/test.php  -- (which does not work). 

If I change the address to... localhost/PHP/test.php
It will render the PHP code just fine. Is there a way to tell the files in var/www to open starting with localhost/?

I'm pretty new to this so any help will be appreciated. Mark

The only way you *can* open PHP files is through the web server (by using [http://localhost](http://localhost) as the address in your web browser).

The server can't be used to open, or execute random files by clicking on them in file manager or anything like that, it has pretty strict configuration about what files and directories it's supposed to use, and it really isn't even made to work for local users opening files from a file manager.

---

