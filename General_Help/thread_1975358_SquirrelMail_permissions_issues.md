---
title: "SquirrelMail permissions issues"
date: 2012-05-07
forum: General Help
---

### Post by fmmarzoa on 2012-05-07
Hi,

I have installed one Ubuntu 10.04 server with ISPConfig 3 and SquirrelMail among other things. Everything is working fine but SquirrelMail does not.

I get an error message like this when I try to login with one of my email accounts:

> Error opening ../config/default_pref
Could not create initial preference file!
/var/lib/squirrelmail/data/ should be writable by user www-data
Please contact your system administrator and report this error.

I have doublechecked that permissions are right. I have even make a 'su www-data' from a terminal, and I was able to access that directory and create a new file with 'touch foo' with no problem, so the problem is not actually on directory permissions, it should be some related with SquirrelMail configuration but I have not been able to find it yet.

Any help will be appreciated.

Best regards,

---

### Post by fmmarzoa on 2012-05-07
I found a solution, although it is not the best one from the point of view of the security, but I did not find nothing best.

Looking at webserver logs I have found that the problem was an open_basedir restriction on PHP, since squirrelmail tries to access several files into /etc and other places that was banned by such restrictions. 

So I ended editing squirrelmail.conf on apache configuration directory and adding this line:


php_admin_value open_basedir "none"

just over the </Directory> closing tag, and now it works perfectly.

Regards,

---

