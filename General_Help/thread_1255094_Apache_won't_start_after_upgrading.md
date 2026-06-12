---
title: "Apache won't start after upgrading"
date: 2009-09-01
forum: General Help
---

### Post by Versusnja on 2009-09-01
hi everybody!

I need help badly!

Server: Ubuntu 8.04.3 LTS 32 bit

I just decided to upgrade all packages. After the upgrade apache won't start. I do not see it listening to any port (with sudo netstat -natp).

When i type sudo /etc/init.d/apache2 start it shows
```
 * Starting web server apache2                                                                                          [Tue Sep 01 10:11:04 2009] [warn] NameVirtualHost *:0 has no VirtualHosts
                                                                                                                 [ OK ]

```
Nothing special really, but it doesn't actually start: there's no lock file and it doesn't listen to port 80.

For a clean check I even used dpkg generic .conf file and deleted all but one 100% working "sites-enabled".

I set log level to "debug", but I don't see a single line in the log file. It's empty. If I delete it, apache creates it again, but doesn't write anything there.

Any ideas where to look for a solution?

I will appreciate any prompt reply!!! This is really urgent

---

### Post by Versusnja on 2009-09-01
So, it was the eaccelerator.

I've commented the following lines in the php.ini:

```
#zend_extension                  = "/usr/lib/php5/20060613+lfs/eaccelerator.so"
#eaccelerator.shm_size           = "16"
#eaccelerator.cache_dir          = "/var/cache/eaccelerator"
#eaccelerator.enable             = "1"
#eaccelerator.optimizer          = "1"
#eaccelerator.check_mtime        = "1"
#eaccelerator.debug              = "0"
#eaccelerator.filter             = ""
#eaccelerator.shm_max            = "0"
#eaccelerator.shm_ttl            = "0"
#eaccelerator.shm_prune_period   = "0"
#eaccelerator.shm_only           = "0"
#eaccelerator.compress           = "1"
#eaccelerator.compress_level     = "9"
#eaccelerator.allowed_admin_path = "/var/www/eaccelerator"

```

Now I need to find how to re-compile the eaccelerator to fit my upgraded php5.

Any help will be appreciated :)

---

