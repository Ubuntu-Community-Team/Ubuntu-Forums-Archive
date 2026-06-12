---
title: "ExpiresActive not allowed here"
date: 2012-01-11
forum: General Help
---

### Post by houmank on 2012-01-11
Hi everyone,

I am pretty much stuck on this and googling for two days without any clear solution to this.

At first it might seem like a wordpress question, but its Apache Linux related, so I hope somebody experienced here can help me.

I am using the plugin W3 Total Cache for Wordpress and as soon as I enable the option:

Performance --> Browser cache --> 'Set expires header' to true

I get a 500 Internal Server Error.

Then I have to SSH into the server and delete the new entries to make the site work again.

Here is the log file, your help is appreciated, as I can't find anything on Google.

```
[Wed Jan 11 07:29:35 2012] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.11 with Suhosin-Patch mod_ssl/2.2.14 OpenSSL/0.9.8k configured -- resuming normal operations
[Wed Jan 11 07:29:38 2012] [alert] [client xxxxx] /var/www/xxx/wp-content/w3tc/min/.htaccess: ExpiresActive not allowed here
[Wed Jan 11 07:29:42 2012] [alert] [client xxxxx] /var/www/xxx/wp-content/w3tc/min/.htaccess: ExpiresActive not allowed here
[Wed Jan 11 07:33:36 2012] [alert] [client xxxxx] /var/www/xxx/.htaccess: ExpiresActive not allowed here, referer: https://www.xxx.com/wp-admin/admin.php?page=w3tc_browsercache
[Wed Jan 11 07:33:36 2012] [alert] [client xxxxx] /var/www/xxx/.htaccess: ExpiresActive not allowed here
```


I have already sudo a2enmod expires

The moment I insert this into the .htaccess file I get the 500 Error again:

```
<IfModule mod_expires.c>
  ExpiresActive On
  ExpiresDefault "access plus 1 hour"
</IfModule>
```

Please help! 
Thanks
Houman

---

