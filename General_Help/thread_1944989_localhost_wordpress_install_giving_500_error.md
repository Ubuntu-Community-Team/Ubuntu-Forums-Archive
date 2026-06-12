---
title: "localhost wordpress install giving 500 error"
date: 2012-03-22
forum: General Help
---

### Post by surrealillusions on 2012-03-22
Hi all,

Got some trouble installing wordpress locally.

Apache, php, mysql, phpmyadmin working fine. All other sites are working fine on the server. Although this is the first one since I've installed mysql that uses mysql. So it maybe that I'm missing some bits, but phpmyadmin works fine.

Anyway, I've tried using 127.0.1.1 and localhost in both the URL's and the wp-config.php file. There is no .htaccess file in the folder, and I've even removed all the spaces from the folder name where wordpress sits.

Importing a database that already works in WP in a live site has no affect, still get the 500 error.

Any ideas?

Thanks.

---

### Post by surrealillusions on 2012-03-22
Found the error logs, and its this one that is probably causing this:

PHP Fatal error:  require(): Failed opening required '/var/www/wordpress/wp-includes/load.php' (include_path='.:/usr/share/php:/usr/share/pear') in /var/www/wordpress/wp-settings.php on line 21, referer: [http://127.0.1.1/wordpress/](http://127.0.1.1/wordpress/)

---

### Post by surrealillusions on 2012-03-23
Any ideas for this please? The file is there in the folder. Google searches are not turning up anything.

---

### Post by surrealillusions on 2012-03-23
Got it eventually, to do with file permissions and ownership on the files and folders.

---

