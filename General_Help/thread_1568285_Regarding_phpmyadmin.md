---
title: "Regarding phpmyadmin"
date: 2010-09-05
forum: General Help
---

### Post by fawzan on 2010-09-05
Hi,
I have installed phpmyadmin on ubuntu 10.04. when i navigate to [http://localhost/phpmyadmin](http://localhost/phpmyadmin) it requires a password and a user name?
what is the default password and username?
or do i have to configure something before that??
Thank you.

---

### Post by Christian Knudsen on 2010-09-05
I found this:

[http://ubuntuforums.org/archive/index.php/t-11695.html](http://ubuntuforums.org/archive/index.php/t-11695.html)

> mysqladmin -u root password "mypassword"

But I think the default username is "root" and the password is blank.

---

### Post by fawzan on 2010-09-09
As Christian Knudsen mentioned > But I think the default username is "root" and the password is blank.  i typed 
Username as root and blank. The below error message appeared.

"Login without a password is forbidden by configuration (see AllowNoPassword)"

---

### Post by Vishal Agarwal on 2010-09-09
it should work with your mysql username login id and password !

---

### Post by indytim on 2010-09-09
1.  If you established a password for the root account when you installed your MySQL Server, use that.

2.  If all else fails, the documentation for the app does wonders:
[http://www.phpmyadmin.net/documentation/]("http://www.phpmyadmin.net/documentation/")

-IndyTim / DataMan

---

