---
title: "Normal solution for“ XAMPP: Another MySQL daemon is already running” not working"
date: 2012-09-02
forum: General Help
---

### Post by southpointingchariot on 2012-09-02
When starting XAMPP, I get the message "XAMPP: Another MySQL daemon is already running.", and MySQL is deactivated in the XAMPP status.

When I try to stop Apache with "sudo /etc/init.d/apache2 stop" I get: "sudo: /etc/init.d/apache2: command not found".

When I try to stop mySQL with "sudo /etc/init.d/mysql stop", I get: "sudo: /etc/init.d/mysql: command not found".

Any thoughts?

---

### Post by Wim Sturkenboom on 2012-09-03
XAMPP is, from this perspective, more than likely not compatible. It installs stuff in /opt if I'm not mistaken, so that's where you will probably find the start and stop scripts.

Do yourself a favour and uninstall it and install a standard mysql/apache/php from the repositories. Then you can follow instructions for Debian/Ubuntu.

---

### Post by southpointingchariot on 2012-09-03
> **Wim Sturkenboom said:**
> XAMPP is, from this perspective, more than likely not compatible. It installs stuff in /opt if I'm not mistaken, so that's where you will probably find the start and stop scripts.

Do yourself a favour and uninstall it and install a standard mysql/apache/php from the repositories. Then you can follow instructions for Debian/Ubuntu.

I'm new to this game - is there a tutorial somewhere on how best to do this?

---

### Post by Wim Sturkenboom on 2012-09-03
A search for *ubuntu lamp install* will get you on the way.

First result is [http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies) which covers install and test; looks quite complete. If everything is on one PC, you can skip the step "gksudo gedit /etc/mysql/my.cnf". It's only necessary if mysql is installed on a different machine than apache.

Plenty of other tutorials available but I did not look further.

---

