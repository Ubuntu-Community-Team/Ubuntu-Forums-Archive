---
title: "Apache2: custom directory listing"
date: 2012-04-26
forum: General Help
---

### Post by megabuffen on 2012-04-26
How can I use a custom header for my apache2 directory listings?

This is my httpd.conf, but it doesn't seem to work:
```
<IfModule mod_autoindex.c>
    IndexOptions FancyIndexing IgnoreCase VersionSort SuppressHTMLPreamble
    HeaderName /home/www/header.html
</IfModule>
```

---

