---
title: "Vague warning from installer (package=mantis)"
date: 2010-10-31
forum: General Help
---

### Post by bkline on 2010-10-31
Just tried installing mantis with "sudo apt-get install mantis" and got the following warning:

> WARNING: include path for php has changed!

libphp-adodb is no longer installed in /usr/share/adodb. New
installation path is now /usr/share/php/adodb.

Please update your php.ini file. Maybe you must also change your
web-server configuraton.

Seems a little vague, assuming there's only one php.ini file on the system and that the user already knows where it is.  Even more vague is the bit about changing your web-server configuration.  Anyone know what they mean by this?

---

