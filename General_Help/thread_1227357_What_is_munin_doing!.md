---
title: "What is munin doing?!"
date: 2009-07-30
forum: General Help
---

### Post by Twizzle on 2009-07-30
I have Ubuntu 8.10 server edition installed and on this I have zarafa, webmin, and zoneminder installed.

I recently noticed a number of munin failed emails in my log files so redirected all munin mail to my account.

I am now getting emails every few minutes as follows:

Subject:Cron <munin@mydomain> if [ -x /usr/bin/munin-cron ]; then /usr/bin/munin-cron; fi

Content:
cp: cannot create regular file `/var/www/munin/': Is a directory
cp: cannot create regular file `/var/www/munin/': Is a directory
cp: cannot create regular file `/var/www/munin/': Is a directory Cannot open /var/www/munin/localdomain/localhost.localdomain-apache_processes.html: No such file or directory at /usr/share/munin/munin-html line 339.


Now, I am sure I have not installed munin and as far as I can se it is a monitoring utility which I had never evern heard of before the emails started arriving.

Can someone please explain, why I am getting these emails and if I can / should remove munin safely?

---

