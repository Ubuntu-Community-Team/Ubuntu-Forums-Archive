---
title: "Php: uploadprogress Not working."
date: 2009-06-27
forum: General Help
---

### Post by ethoxyethaan on 2009-06-27
SOLVED: mod_security caused the problem. 

Hello i installed uploadprogress.so and added it to php.ini but its not working:

uploadprogress_get_info($id); returns NULL



```
root@mm-rs:/etc/csf# find /usr/ | grep uploadprogress
/usr/share/php/docs/uploadprogress
/usr/share/php/docs/uploadprogress/examples
/usr/share/php/docs/uploadprogress/examples/index.php
/usr/share/php/docs/uploadprogress/examples/server.php
/usr/share/php/docs/uploadprogress/examples/info.php
/usr/share/php/.registry/.channel.pecl.php.net/uploadprogress.reg
/usr/lib/php5/20060613/uploadprogress.so

```

inside php.ini:
```
extension_dir = "/usr/lib/php5/20060613/"
extension="uploadprogress.so"

```

can someone help me / explain why its still not working.

---

### Post by sweb on 2010-04-27
Also i have to compile my php by myself and have a same problem.
Any one can help us?

---

