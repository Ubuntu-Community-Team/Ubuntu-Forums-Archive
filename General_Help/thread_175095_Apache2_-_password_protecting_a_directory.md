---
title: "Apache2 - password protecting a directory"
date: 2006-05-12
forum: General Help
---

### Post by northface on 2006-05-12
Have created a passwordfile using the htpasswd utility and have put the passwordfil in /etc/apache2/. My .htaccess is in /var/www/foldertoprotect/.

The .htaccess looks like this;
AuthType Basic
AuthName "Restricted Files"
AuthUserFile /etc/apache2/name_of_passwordfile
Require user name_of_user

But I can't get it to work.](*,)  When surfing to the foldertoprotect the password dialog box doesn't appear.

 When looking into /etc/apache2/mods-availible and mods-enabled I can't find mod_auth_basic. Should it be there?

Could anyone help? Thanks.

---

### Post by henriquemaia on 2006-05-12
Have you consulted the Apache's documentation site? 

[http://httpd.apache.org/docs/2.0/howto/htaccess.html](http://httpd.apache.org/docs/2.0/howto/htaccess.html)

I followed the procedures listed there and got it to work.

---

### Post by northface on 2006-05-12
Yes. Did you change anything in apache2.conf ? 
Anything like;
<Directory /path_to_.htpasswd>
AllowOverride All
</Directory>

---

### Post by henriquemaia on 2006-05-12
[QUOTE=northface]Yes. Did you change anything in apache2.conf ? 
Anything like;
<Directory /path_to_.htpasswd>
AllowOverride All
</Directory>[/QUOTE]

No. Actually, I just added the folders I wanted to be protected into httpd.conf . 

Here's my as an exemple:

<Directory /directory/to/be/protected>
	AuthType Basic
	AuthName "Put here whatever message you want"
	AuthUserFile /etc/apache2/passwords
	Require valid-user
</Directory>

After reading the apache's documentation, I found this was a better solution.

---

### Post by northface on 2006-05-13
Ok, finally I got it to work.

1. Created a passwordfile using the htpasswd utility and put the passwordfil in /etc/apache2/
2. Added the following lines in apache2.conf
<Directory /var/www/folder_to_protect>
AuthType Basic
AuthName "Restricted Files"
AuthUserFile /etc/apache2/name_of_passwordfile
Require user name_of_user
</Directory>
3. No .htaccess file in the folder to protect!

Thanks for your response!

---

### Post by rasti121 on 2006-12-12
I did the same, but still doesn't work getting: 
... configuration error:  couldn't check user.  No user file?:... in appache error log (user file exists and has users created with htpasswd). Anyboyd have solved this?

apache2.conf:
...
<Directory /var/www/restricted>
AuthType Basic
AuthName "Restricted Files"
AuthUserFile /etc/apache2/htpass
AllowOverride All
Require valid-user
</Directory>

---

### Post by gmconie on 2007-04-03
[https://help.ubuntu.com/community/EnablingUseOfApacheHtaccessFiles](https://help.ubuntu.com/community/EnablingUseOfApacheHtaccessFiles)

This page details how to activate .htaccess.

mod-auth--basic not requried.

---

### Post by K_Man on 2007-04-17
I was having the same issues and discovered that the config file /etc/apache2/sites-available/default has the option AllowOverride None.  I changed it to AllowOverride to All and my .htaccess file started working.

---

