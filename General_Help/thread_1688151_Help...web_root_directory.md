---
title: "Help...web root directory"
date: 2011-02-15
forum: General Help
---

### Post by akemzo on 2011-02-15
Hi, anyone know what the web root directory and path is in xampp? Installed a script but it don't work:

$web_path = "/opt/lampp/htdocs/"; // INCLUDE TRAILING SLASH /

$web_root = "home/akemzo//opt/lampp/"; // should be in /home/youruser/public/ format

What am i doing wrong here?

Error i get trying to run my script:

Warning: require_once(home/akemzo//opt/lampp/functions/settings.php) [function.require-once]: failed to open stream: No such file or directory in /opt/lampp/htdocs/avs/config/connection.php on line 24

Fatal error: require_once() [function.require]: Failed opening required 'home/akemzo//opt/lampp/functions/settings.php' (include_path='.:/opt/lampp/lib/php') in /opt/lampp/htdocs/avs/config/connection.php on line 24

---

### Post by blueridgedog on 2011-02-15
```
This:

$web_root = "home/akemzo//opt/lampp/";
```

Has a typo, and should no doubt be:

```
$web_root = "/home/akemzo/opt/lampp/";
``` 

This assumes you have made the directories in your home directory as stated and moved the essential files there.

---

