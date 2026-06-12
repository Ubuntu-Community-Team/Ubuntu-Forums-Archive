---
title: "Mod_rewrite in virtual host (Apache2)"
date: 2012-02-14
forum: General Help
---

### Post by Abadon125 on 2012-02-14
So this is not an Ubuntu question (I am actually running arch) but the community here has been very helpful to me in the past so I thought I would ask here anyway.

I have mod_rewrite working just fine for files that are in /srv/http. I copied my test files to another directory where I have an alias pointing and tried them there but was not able to get it working. Is anyone able to spot what I am doing wrong? Here are my configs:

Relevant portions of httpd.conf
```
Alias /tv "/home/username/a/folder/path"
<Directory "/home/username/a/folder/path">
        Order allow,deny
        Options FollowSymLinks
        Allow from all
        AllowOverride All
</Directory>

```

Let me know if there are other files that would help.

Later, after doing a bit more research I found this in the codeigniter wiki. I am trying to get codeigniter installed and running on my.ip.address/tv. It seems that the mod_rewrite stuff can be done in the http.conf file. Scroll to the very bottom to see what I am talking about.
[http://codeigniter.com/wiki/mod_rewrite](http://codeigniter.com/wiki/mod_rewrite)

So going off of that, here is what I am trying to use. Please let me know which portion I need to change if you can spot any problems. 
```
Alias /tv "/home/username/a/folder/path"
<Directory "/home/username/a/folder/path">
        Order allow,deny
        Options FollowSymLinks
        Allow from all
        AllowOverride All
         RewriteEngine On
                RewriteBase /
                RewriteCond %{REQUEST_FILENAME} !-f
                RewriteCond %{REQUEST_FILENAME} !-d
                RewriteRule ^(.*)$ index.php/$1 [L]
</Directory>

```

Thanks!

---

