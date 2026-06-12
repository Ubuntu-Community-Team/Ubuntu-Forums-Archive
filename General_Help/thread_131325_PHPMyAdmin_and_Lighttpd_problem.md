---
title: "PHPMyAdmin and Lighttpd problem"
date: 2006-02-16
forum: General Help
---

### Post by foof on 2006-02-16
I've installed Lighttpd 1.4.9 and MySQL5 without problem.
Now I also installed PHPMyAdmin from the package manager and got it working, but since it automatically installs Apache I had to remove all Apache packages.
Now the package manager (Adept) says PHPMyAdmin is broken, but it still works in my Lighttpd webserver so that is'n a big problem, but what is a big problem is when I try to add php extensions to my Lighttpd/PHP server it fails and can't install them. What can I do to fix this?

---

### Post by foof on 2006-02-16
Well I got it working by following this:

Originally Posted by Surfoo
Edit /var/lib/dpkg/info/phpmyadmin.prerm and before the comment "# Package maintainer's commands follow:", add this line :

. /usr/share/debconf/confmodule

without forget the point.
Save, and after apt-get remove phpmyadmin

Then I just downloaded the latest phpmyadmin source and put the files where it was before /usr/share/phpmyadmin
Then I edited config.default.php and got it working again. But in the package manager it says it's not installed... but that's ok I guess.

---

### Post by moon2js on 2007-04-27
> **foof said:**
> I've installed Lighttpd 1.4.9 and MySQL5 without problem.
Now I also installed PHPMyAdmin from the package manager and got it working, but since it automatically installs Apache I had to remove all Apache packages.

How did you get phpmyadmin to work on lighttpd?

---

