---
title: "Cgi-bin in /var/www to work"
date: 2010-07-18
forum: General Help
---

### Post by undertai on 2010-07-18
I have been trying to get my cgi-bin from /var/lib to /var/www my web servers directory.  I used webmin as I run 10.04 lts server on a laptop.  So I either ssh or use webmin to changes stuff on my ubuntu box.  Using webmin I copied every directive from the /var/lib to my new one.  But my cgi or pl files want work.  Anyone know of anther way to get it to work?

---

### Post by Vishnu V on 2010-07-19
Default Drectory of cgi-bin is 
/usr/lib/cgi-bin/

---

### Post by gmargo on 2010-07-19
You can put a cgi-bin under /var/www but then you have to update your apache configuration.  See the files under /etc/apache2/sites-enabled, which probably points to /etc/apache2/sites-available/default.  Now look in that file and search for cgi-bin.  Now you can see an "Alias" and "Directory" directive that gives /usr/lib/cgi-bin it's permissions.  You'll need to make a similar entry for the /var/www/whatever/cgi-bin directory.

---

### Post by undertai on 2010-07-19
I did copy the directives from the /usr/lib/cgi-bin.  But I got the following error after restarting apache2

The ScriptAlias directive in /etc/apache2/sites-enabled/000-default at line 41 will probably never match because it overlaps an earlier ScriptAlias.

---

