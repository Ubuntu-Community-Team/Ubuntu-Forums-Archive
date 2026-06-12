---
title: "Apache 2 not using custom error pages"
date: 2009-07-20
forum: General Help
---

### Post by Kopachris on 2009-07-20
I have Apache 2 installed on my Ubuntu 9.04 Desktop with the latest PHP and MySQL.  I made a .htaccess file with ```
ErrorDocument 404 error404.php
``` and made the error404.php file.  When I go to [http://localhost/error404.php](http://localhost/error404.php), it displays just like it should.  When I go to a page that's not there ([http://localhost/noexist.php](http://localhost/noexist.php)), I get the default Apache 404 message.  Why isn't it showing the custom message?

---

