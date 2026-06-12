---
title: "Informix PDO and PHP"
date: 2012-01-25
forum: General Help
---

### Post by chaos22 on 2012-01-25
I'm using PHP 5.3.2, Ubuntu 10.04.3 LTS, and Informix which is on a seperate server.  I have read through a ton of things involving using pecl and pear to install the pdo, recompiled php without a pdo option, blah blah blah.  Has anyone ever gotten this setup to work?  I seems like everytime I get to one point, there is another hurdle.

---

### Post by chaos22 on 2012-01-25
Sorry about the lack of information.  Too much thinking today.  I need to use pdo to connect php to informix, because I already have an app written using pdo and I want to put it on Ubuntu.  There seems to be problems with PDO_informix and the newest versions of PHP.  I'm going to try and load an older dev of php.  If anyone has any other ideas before I break something it would be much appreciated.

---

### Post by SeijiSensei on 2012-01-25
I presume you've read this already?

[http://www.php.net/manual/en/ref.pdo-informix.php](http://www.php.net/manual/en/ref.pdo-informix.php)

How about that requirement that the "Informix Client SDK 2.81 UC1 or higher must be installed on the same system as PHP" in order to build the module?

---

