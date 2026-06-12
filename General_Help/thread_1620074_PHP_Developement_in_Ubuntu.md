---
title: "PHP Developement in Ubuntu"
date: 2010-11-12
forum: General Help
---

### Post by jamest10 on 2010-11-12
I am starting to develop websites in Ubuntu. I have set up apache server, php, mysql, and phpmyadmin. I have also set up a local domain for the site. Everything works great with html files, but how do I get Firefox to open .php files instead of trying to save them.

Thanks

---

### Post by blueridgedog on 2010-11-12
Files containing php code must be served by a web server that can run them through the php processing engine and the web server has to be configured to handle php pages.  If you are trying to get a result from a php page through a web server and your browser is trying to save the php page, then the web server is not handling the php page correctly.

---

### Post by jamest10 on 2010-11-13
I tested php files now in my /var/www directory(were localhost point to) and they work fine but the apache server must not be treating php files properly in the local domain I set up. This is the guide I followed to set up the local domain.

[http://kimbriggs.com/computers/computer-notes/linux-notes/apache2-public_html-virtual-directories.file](http://kimbriggs.com/computers/computer-notes/linux-notes/apache2-public_html-virtual-directories.file)

what can I do to get apache to treat the directory attached to my local domain properly?

---

