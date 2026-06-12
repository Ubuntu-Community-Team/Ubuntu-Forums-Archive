---
title: "PHP Memory Allocation"
date: 2011-01-09
forum: General Help
---

### Post by Norfavrell on 2011-01-09
Hello. I recently had to move to a new machine, everything went well except for one thing. I did fresh installation of LAMP server all with default configs. Every time I'm using PHP script to that invokes include, require or require_once I get the following error:
```
Fatal error: Allowed memory size of 20971520 bytes exhausted (tried to allocate 7680 bytes) in /var/www/index.php on line 2
```

index.php file:[PHP]<?php
	include "index.php";
?>
[/PHP]

icukapi.php file:[PHP]<?php
	echo "test";
?>
[/PHP]

My memory_limit in php.ini is set to 20M. I tried to increase that however it didn't quite work. PHP seems to allocate all possible space and return that message every time i try. 

If somebody has an idea of how to fix it I would be more than grateful. I spend quite a long time searching for an answer however the all things i found suggested increating memory_limit which in this case doesn't work.

Kind Regards,
norfavrell

---

### Post by gopakumar.s on 2011-05-25
Hi,
 
The default resource usage limit of your PHP is depended on your Linux distribution. Normally it can be 8M or 16M. 
 
Changing the value in ***php.ini*** file will have a global effect on your system ie it can have an effect on all PHP scripts running on your system. You need to restart Apache to get this change reflected.
 
```
memory_limit = 64M
``` 
 
If you run the script on a virtual host, try adding adding the new memory value to the ***.htaccess*** file at the respective folder of the vhost. The change should be reflected immediately and it will have only a local effect on that particular folder or vhost. Apache restart not required.
 
```
php_value memory_limit 64M
```
 
You can also specify the memory limit inside a PHP script. The change should be reflected immediately and it will have an effect only on that single script. Apache restart not required.
 
```
ini_set('memory_limit', '64M');
```
 
Please keep in mind that, if you want to change your PHP memory limits from default, your PHP version must be compiled with ***–enable-memory-limit*** when you configure it. If your memory limit change won't get effected, check how your PHP was compiled.
 
Hope this may help.

---

