---
title: "xampp - cURL"
date: 2010-10-06
forum: General Help
---

### Post by 0000_soldier on 2010-10-06
Hello,

*sorry if this goes in another section - thought it was  suited here.

Can anyone help me activate the cURL library on xampp i have had issues trying to do it. I could not open the php.ini file and edit it I tried using chmod and chown but im new to linux an still get problems, when running xampp from the terminal it saids cURL directory does not exist. ps I did look around for solutions on the net found some partial relevant that did not help.

since trying to install cURL from the synaptic package manager php5-cURL i ran in to more errors, daemon still running so i uninstalled it and xampp.

Thanx any help appreciated! - where did i go wrong?

---

### Post by 0000_soldier on 2010-10-06
The only php.ini file I find is under the etc/ folder and if I uncomment the extension=php_curl.dll...my XAMPP errors when I start up the server:

```


Starting XAMPP for Linux 1.7...
PHP Warning: PHP Startup: Unable to load dynamic library '/opt/lampp/lib/php/extensions/no-debug-non-zts-20060613/php_curl.dll' - /opt/lampp/lib/php/extensions/no-debug-non-zts-20060613/php_curl.dll: cannot open shared object file: No such file or directory in Unknown on line 0
XAMPP: Starting Apache with SSL (and PHP5)...
XAMPP: Starting MySQL...
XAMPP: Starting ProFTPD...
XAMPP for Linux started.



```

---

### Post by 0000_soldier on 2010-10-08
**i found a user with the same problem on another website in a google.Anyway I finally think I have solved this, I think I may have accidentally execute a bash script i made to reinstall xampp.

After reading a bit about Debian (in a book i got for free), I found that daemons are kept in the /etc in the root direction, i looked further and found the "/opt/lampp" of xampp in there aswell as having it installed as root directory /opt. i opend the  terminal and typed ```
cd etc
``` and then typed ```
 ls -a
``` i found the /opt/lampp/lampp in there too then typed while in the/etc directory ```
rm -r opt
``` removing all the recursive directories. Then i restarted the server and the error no longer seems to happen.

---

