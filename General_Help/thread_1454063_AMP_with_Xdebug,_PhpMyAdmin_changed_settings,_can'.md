---
title: "AMP with Xdebug, PhpMyAdmin changed settings, can't set back to correct php.ini"
date: 2010-04-14
forum: General Help
---

### Post by Vordreller on 2010-04-14
I installed apache, php and xdebug using a video tutorial, found here: [http://vimeo.com/8005503](http://vimeo.com/8005503)

All worked fine. A simple file with [PHP]<?php phpinfo(); ?>[/PHP]Showed that xdebug was configured correctly.

After this, I installed mysql-server and PhpMyAdmin, both via the Synaptic Packet manager.

PhpMyAdmin, upon installation, will offer to modify apache2 in order to work successfully with it. So I did, since I have no idea how to set this manually.

However, the path to the php.ini file was now changed and Xdebug is no longer included. I changed the content of the now used php.ini file to be a copy of the previous working php.ini file, but this had no effect.

My old path was /etc/php5/php.ini

The new path is /etc/php5/apache2/php.ini

Yet, even with identical content, it's still not working.

---

