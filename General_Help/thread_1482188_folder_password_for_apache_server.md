---
title: "folder password for apache server"
date: 2010-05-13
forum: General Help
---

### Post by group256 on 2010-05-13
Hi,

I just tried to make one of my folders password protected. It's an apache server running on Ubuntu server 9.10. I created the .htaccess and .htpasswd file in my folder which I want to hide, and I modified /etc/apache2/httpd.conf to allow authentication.

.htpasswd is:

```
AuthUserFile /var/www/test/.htpasswd
AuthType Basic
AuthName "My Secret Folder"
Require valid-user
```

my httpd.conf is like:

```

<Directory /var/www/test>
AllowOverride AuthConfig
</Directory>

```

Now the problem is that, my folder is invisible in my browser. I can see it using WinSCP but in firefox, the folder is hidden.

Any ideas???

Thanks a lot.

---

### Post by PingBomb on 2010-05-13
<Directory '/var/www/test'>
AuthType Basic
AuthName "My Secret Folder"
AuthUserFile /var/www/test/.htpasswd
Require valid-user
</Directory>


Require valid-user i recommend to be Require user SOME_USER_NAME :)
that's look like more secure.

---

### Post by group256 on 2010-05-13
Thanks, 

But it still doesn't fix the problem. Anything else??

---

### Post by alienprdkt on 2010-05-13
> **group256 said:**
> Thanks, 

But it still doesn't fix the problem. Anything else??

well you could do it the way I do and create a mysql php login form :D

---

### Post by PingBomb on 2010-05-14
Did u have this line in httpd.conf

allow from all
or 
Allow from SOME_IP


example:

<Directory /var/www/test>
allow from all
Options -Indexes
</Directory>

Also please check:

/etc/apache2/sites-available/default (not sure it was correct path)

---

