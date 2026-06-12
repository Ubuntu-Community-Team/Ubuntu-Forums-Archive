---
title: "I'm attempting to run a script by launching it daily from the(include path problems)"
date: 2009-12-21
forum: General Help
---

### Post by bar338 on 2009-12-21
I'm attempting to run a script by launching it daily from the crontab. The script works fine when I call it from the browser. However, whenever the crontab attempts to initiate the script it gets an error.
Warning: require_once(/pathtomyscript/includes/co… failed to open stream: No such file or directory in /pathtomyscript/cron.php

Apparently the crontab has difficulties with executing scripts that contain relative paths. To fix this I tried changing the path to an absolute path like /home/www/public_html/pathtoscript/inclu… however this gives me the error of illegal include. How should I control my include paths so that they work with the cron tab?

The scripts are owned by root and the cronjob is executed by root.

I'm using mysql and the sphider php search engine.  The indexing script has some degree of complexity.

Shouldn't I be able to adjust the include path so that the crontab located in
/etc/crontab 
can call the index script in 
/home/www/public_html/search/admin/cron_index.php
and the cron script can include a config file at:
/home/www/public_html/search/includes/config.conf

The script does not have to be accessible to anything other than the crontab. It is in the search directory just to keep it in close proximity with all the search elements.

Thanks for your help with understanding why the paths don't work and what I can do to fix them.

---

