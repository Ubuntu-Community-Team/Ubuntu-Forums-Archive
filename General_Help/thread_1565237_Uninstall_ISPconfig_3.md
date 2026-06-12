---
title: "Uninstall ISPconfig 3"
date: 2010-08-31
forum: General Help
---

### Post by dbrine on 2010-08-31
I am trying to uninstall ISPConfig3 but haven't found anything yet?? I am not able to login either, says password, etc incorrect. 

Besides a complete format how do I uninstall?


thanks,

---

### Post by dbrine on 2010-09-02
no one?

---

### Post by Autodidact on 2010-09-02
Just run the uninstall.php file that came with ISPConfig3. Do something like:

Open terminal and 'cd' to the directory where ISPConfig3 has been installed.
Then run:
```
php -q uninstall.php
```

---

### Post by acc61287 on 2011-11-08
> **Autodidact said:**
> Just run the uninstall.php file that came with ISPConfig3. Do something like:

Open terminal and 'cd' to the directory where ISPConfig3 has been installed.
Then run:
```
php -q uninstall.php
```

Make sure you backup your /etc/apache2/apache2.conf.. because after you uninstall ispconfig your apache2 encounter a problem, it wont start..If any one who encounter this problem, follow this steps:
1. backup apache2.conf ( As I mention earlier)
2. Uninstall ispconfig
3. sudo a2dissite 000-apps.vhost
4. sudo a2dissite 000-ispconfig.conf

if you got this error:
ERROR: Site 000-apps.vhost does not exist!
ERROR: Site 000-ispconfig.conf does not exist!

you may remove them from /etc/apache2/site-enabled/
sudo rm /etc/apache2/site-enabled/000-apps.vhost
sudo rm /etc/apache2/site-enabled/000-ispconfig.conf

this is what I did :)

But I guess, It's better to disable 000-ispconfig.conf and 000-apps.vhost before you uninstall ispconfig 3

I hope, It will help for those who encounter that problem

---

