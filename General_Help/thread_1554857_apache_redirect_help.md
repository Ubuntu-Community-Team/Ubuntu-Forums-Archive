---
title: "apache redirect help?"
date: 2010-08-17
forum: General Help
---

### Post by SlugSlug on 2010-08-17
Hi All,
I have two domain names (name1 & name2). [http://name1.com](http://name1.com) & [http://name2.com](http://name2.com) both go to my server at /var/www

I would like it if name1 would get forwarded to name2 as am trying to phase out name1

My .htaccess file currently is 

```
Options +FollowSymLinks
RewriteEngine on

RewriteCond %{HTTP_HOST} ^(www\.)?name1\.com [NC]
RewriteRule ^(.*)$ http://www.name2.com/$1 [L,R=301]

RewriteCond %{HTTP_HOST} ^name1\.com [NC]
RewriteRule ^(.*)$ http://www.name2.com/$1 [L,R=301]

RewriteCond %{HTTP_HOST} ^name1\.com [NC]
RewriteRule ^(.*)$ http://www.name2.com/$1 [L,R=301]
```

and with that in place I get "Internal Server Error"

can anyone help?

---

### Post by SlugSlug on 2010-08-18
bump :popcorn:

---

