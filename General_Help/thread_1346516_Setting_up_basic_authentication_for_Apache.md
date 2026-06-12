---
title: "Setting up basic authentication for Apache"
date: 2009-12-05
forum: General Help
---

### Post by lethalfang on 2009-12-05
I did the following: 

sudo htpasswd -c /var/passwd/passwords allowed_user

Then, I added the following to the  /etc/apache2/httpd.config

<Directory /var/www/secret_folder>
AuthType Basic
AuthName "Restricted Files"
AuthUserFile /var/passwd/passwords
Require user allowed_user
</Directory>


I restarted by
sudo /etc/init.d/apache2 restart

... but the authentication system isn't kicking in.

What did I miss?

Thanks in advance.

---

### Post by lethalfang on 2009-12-05
Silly me, the file should be httpd.**conf**, instead I've created httpd.**config**.

---

