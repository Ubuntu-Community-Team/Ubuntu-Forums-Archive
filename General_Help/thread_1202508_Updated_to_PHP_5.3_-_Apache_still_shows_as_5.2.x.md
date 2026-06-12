---
title: "Updated to PHP 5.3 - Apache still shows as 5.2.x"
date: 2009-07-02
forum: General Help
---

### Post by markux^Hs on 2009-07-02
I just updated my local server to PHP 5.3 - Downloaded the source, dir ./configure make make install, etc.

If I run *php -v *at the command line, it shows, as I would expect:
> PHP 5.3.0 (cli) (built: Jul  2 2009 15:32:06) (DEBUG)
Copyright (c) 1997-2009 The PHP Group
Zend Engine v2.3.0, Copyright (c) 1998-2009 Zend Technologies


However, when doing *phpinfo()* via my apache server, the PHP version shows up as 
**[SIZE=1]> PHP Version 5.2.6-3ubuntu4.1[/SIZE]**

Is there anything else I have to do to inform apache of the new PHP?

What I don't understand is: prior to download PHP 5.3, there wasn't any PHP installed (I just did a clean install of Ubuntu). That leads me to believe that apache does not use the php from the $PATH variable, but possibly the libapache2-mod-php5 ... maybe?

Thanks, guys n gals.

---

### Post by Tibuda on 2009-07-02
libapache2-mod-php5 depends on the php5-common package. I think you have the repos php in /usr/bin and the source php in /usr/local/bin. Try running
```
/usr/bin/php -v
which php
```
in a terminal.

---

