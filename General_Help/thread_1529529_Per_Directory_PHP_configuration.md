---
title: "Per Directory PHP configuration"
date: 2010-07-12
forum: General Help
---

### Post by jcobban on 2010-07-12
I wish to set some PHP configuration options on a per-directory basis.

phpinfo says Server API = 'Apache 2.0 Handler'.  Therefore I believe that the configuration options should be placed in the .htaccess file.  I created a .htaccess file containing the following:

<IfModule mod_php5.c>
include_path = ".:/usr/lib/php:/usr/local/lib/php:/home/jcobban/php"
extension_dir = "/usr/local/lib/php/extensions/no-debug-non-zts-20060613"
magic_quotes_gpc = "0"
extension="suhosin.so"
suhosin.post.max_vars = 2000
suhosin.request.max_vars = 5000
display_errors = "On"
</IfModule>

But phpinfo shows none of these options taking effect.

What do I have to do to configure PHP support in this directory.

---

