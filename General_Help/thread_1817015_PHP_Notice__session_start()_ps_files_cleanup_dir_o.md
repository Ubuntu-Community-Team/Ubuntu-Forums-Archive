---
title: "PHP Notice:  session_start(): ps_files_cleanup_dir: opendir(/var/lib/php5) failed:"
date: 2011-08-02
forum: General Help
---

### Post by withjigs on 2011-08-02
Hi All,
I installed Cacti 0.8.7g on Ubuntu Lucid 10.04.
While trying [http://serverip/cacti/](http://serverip/cacti/) I didn't get anything on the page.
I checked the apache2 error log and found an entry saying

```
PHP Notice:  session_start(): ps_files_cleanup_dir: opendir(/var/lib/php5) failed: Permission denied (13) in /var/www/cacti/include/global.php on line 145, referer: http://server_ip_address/

```

I searched on the internet and found that it has something to do with how Ubuntu/Debian handles garbage collection. 

some suggests that changing gc_probability in php.ini to zero could be solution. 

As, this is a production server, I should be 100% sure before I make any changes. 

Thank for your help!

Jigar

---

### Post by maxim_86ualb2 on 2011-08-08
I solved the in a tad different way. What I did was change the group of /**var/lib/php5** to www-data, and allowed group read and write access.

---

