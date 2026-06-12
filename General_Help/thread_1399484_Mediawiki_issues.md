---
title: "Mediawiki issues"
date: 2010-02-05
forum: General Help
---

### Post by Tomasthanes on 2010-02-05
I installed and patched Ubuntu Desktop AMD64 9.10.  I then installed the (L)AMP stack following the directions in [http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-9.10-lamp](http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-9.10-lamp).  I then installed and configured mediawiki (1.15.0) following the directions at [https://help.ubuntu.com/9.10/servereguide/C/mediawiki.html](https://help.ubuntu.com/9.10/servereguide/C/mediawiki.html).

At this point, the mediawiki Main_Page displays just fine.  However, if I want to edit a page for view the Special Pages, the resulting output is empty.  View Source shows no data in the page.

I'm looking for assistance in troubleshooting this problem as I don't see any failure in the /var/log/syslog or in the Apache2 access.log or error.log.

Any suggestions?  I'd love to get this working as it would provide me a much faster wiki that what I'm working right now on my old Sun Ultra 10 server.

TIA

---

### Post by Tomasthanes on 2010-02-07
This problem is now resolved.  There were 2 problems: errors were not being displayed and the default memory limit was too low for mediawiki.

To address the display of errors, add the following lines to the top of /etc/mediawiki/LocalSettings.php

error_reporting( E_ALL );
ini_set( 'display_errors', 1 );

To address the memory limit issue, edit /etc/php5/apache2/php.ini and find the line that looks like:

memory_limit = 20M      ; Maximum amount of memory...

Change the "20M" to "32M".

Next, edit /etc/mediawiki/LocalSettings.php and find the lines that looks like:

# If PHP's memory limit is very low, some operations may fail.
ini_set( 'memory_limit', '20M' );

Change the '20M' to '32M'.

Now, restart Apache (though the guy on the mediawiki forum said that this is optional).

---

