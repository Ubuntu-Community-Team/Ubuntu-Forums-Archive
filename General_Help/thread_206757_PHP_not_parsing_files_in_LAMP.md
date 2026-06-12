---
title: "PHP not parsing files in LAMP"
date: 2006-06-30
forum: General Help
---

### Post by brianbarry on 2006-06-30
I've got Apache2, MySQL 5, and PHP5 installed, via apt-get.  In a moment of pure lunacy I installed the Apache2 PHP4 library and PHP stopped parsing *.php.  I've completely uninstalled the PHP4 library to no avail.  I've even reinstalled PHP5 and Apache2, again via apt-get...same issue.  The PHP5 module is enabled and dependent modules are indeed present but I'm still presented with the prompt as to what I'd like to do with the *.php file.

Any assistance would be greatly appreciated,
Brian Barry

---

### Post by nix4me on 2006-06-30
Use the instuctions for apache+php+mysql in the wiki.  Just searh apache from the wiki search bar.

It tells you exactly how to get it working.  I had a similar problem and i just removed everything php and mysql and re-installed using the wiki instructions.

Worked for me.

nix4me

---

### Post by az on 2006-06-30
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

