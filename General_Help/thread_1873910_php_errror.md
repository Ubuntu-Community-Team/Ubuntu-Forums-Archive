---
title: "php errror"
date: 2011-11-02
forum: General Help
---

### Post by Angelojoseph17 on 2011-11-02
I get an error when executing any php script , it works but i still want to know why i get this error. 



<pre>[/HTML]PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/cli/conf.d/mcrypt.ini on line 1 in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20090626+lfs/snmp.so' - /usr/lib/php5/20090626+lfs/snmp.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP 5.3.2-1ubuntu4.10 with Suhosin-Patch (cli) (built: Oct 15 2011 00:09:58)
Copyright (c) 1997-2009 The PHP Group
Zend Engine v2.3.0, Copyright (c) 1998-2010 Zend Technologies
You have new mail in /var/mail/root </pre>

---

### Post by goodvikings on 2011-11-02
Most of those are pretty self explanatory, like the comment no longer by a '#' symbol.

Also, the last line isn't a PHP error. You just have mail.

---

### Post by Angelojoseph17 on 2011-11-02
No I'm talking about the php warning line ....

---

### Post by alco75 on 2011-11-02
Well, PHP can't find **snmp.so**, maybe something in **php.ini** is expecting it to be there? Have a look at **phpinfo()** and search the page for **snmp**.

Maybe the **php5-snmp** package isn't installed? Run:

```
dpkg -l | grep -i snmp
```

---

