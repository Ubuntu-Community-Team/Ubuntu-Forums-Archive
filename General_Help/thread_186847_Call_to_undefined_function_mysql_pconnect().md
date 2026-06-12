---
title: "Call to undefined function: mysql_pconnect()"
date: 2006-06-02
forum: General Help
---

### Post by Migalicious on 2006-06-02
Hello, I'm trying to set up Snort using the tutorial <a href="http://www.ubuntuforums.org/showthread.php?t=145641&highlight=snort">here</a>
And I'm at the point where you need to run the Base configuration.  I go to [http://localhost/base/base_main.php](http://localhost/base/base_main.php) on my machine and I get the error:

> 
Fatal error: Call to undefined function: mysql_pconnect() in /usr/share/php/adodb/drivers/adodb-mysql.inc.php on line 372


I checked the line, and I think I see the problem, it keeps referencing $this, but I don't see it defined anywhere in the file.

I tried reinstalling php-mysql, as well as running dpkg-reconfigure php5-mysql.  Is there an easy fix for this or should I just uninstall all my packages relating to snort, mysql, base, etc and start from scratch?

---

### Post by Migalicious on 2006-06-02
I purged EVERYTHING (even though mysql didn't purge completely, all my databases and tables were there for snort from before), and instead of using Synaptic to install the packages, I used the command line verbatim from the HOWTO, and it now works.

One caveat though, for anyone else that tries this.  Before you try the base install, you MUST reboot.  I tried restarting apache, snort, and mysql, but I still got the error until I rebooted the machine.

---

