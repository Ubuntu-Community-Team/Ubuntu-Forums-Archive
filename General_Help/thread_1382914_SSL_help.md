---
title: "SSL help"
date: 2010-01-16
forum: General Help
---

### Post by millergroup on 2010-01-16
Hi

I am running Ubuntu Linux 6.06.2. Trying to get SSL virtual host to work. Everything is installed with a self singed cert.

When going to [https://mysite](https://mysite) it brings my to the default apache index page instead of staying on my site. I am having a path problem and cannot find that problem. Can someone provide a clear instruction to point my Vhost to the proper path?

Thank you in advance.

---

### Post by jonesman on 2010-01-17
I am installing a new ssl server this weekend too.  Just a thought, it looks like you are using an older distro; if you are also using Apache 1.4 you might consider upgrading to Apache2.  It sounds like there were some improvements that made configuration easier.  If not, check /etc/apache2/site-available/default and default-ssl to see if both VirtualHosts have the same DocumentRoot (/var/www in mine).  If they had the same root the same page would come up. jones

---

### Post by HighCommander540 on 2010-01-17
Go [here]("http://ubuntuforums.org/forumdisplay.php?f=339"). Then befriend the search button. That is all you are going to get. There have been a million threads about this.

---

