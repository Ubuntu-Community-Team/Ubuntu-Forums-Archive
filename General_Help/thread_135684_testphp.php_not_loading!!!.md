---
title: "testphp.php not loading!!!"
date: 2006-02-24
forum: General Help
---

### Post by moutraji on 2006-02-24
Hello guys!!!! I'v a littel problem here!!! my testphp.php is not loading but when i try to open it through [http://localhost/testphp.php](http://localhost/testphp.php) the php code in the testphp is displayed. On the other hand, when i try to open [http://localhost](http://localhost), it is working in which it is showing me what i have in there and that are testphp.php, apache2-default, and webalizer... Any help please!!! thank you!!!

---

### Post by encompass on 2006-02-24
I think that is what it is supposed to do... by default it will automaticly load a file list if it does not see an index.html file.  so it is working just fine.  unless your talking about something completely different.

---

### Post by moutraji on 2006-02-24
Will!!! You know the configuration information page that suppose to be displayed with the information about php, mysql, apache and all the stuff that are enabled??? How that suppose to be displayed??? Its not being displayed???

---

### Post by moutraji on 2006-02-24
thanks any way, i got it fixed!!! I just had to uncomment the lines that are in /etc/apache2/apache2.conf file:
AddType application/x-httpd-php .php
AddType application/x-httpd-php-source .phps
that's all!!!!

---

