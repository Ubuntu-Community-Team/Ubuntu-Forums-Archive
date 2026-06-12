---
title: "Apache Log size"
date: 2009-09-19
forum: General Help
---

### Post by elliotbeken on 2009-09-19
Hi all, 

this is a silly question but i have apache2 running and i would like to change the log file so it is bigger (therefore holding more information)

i have had a quick look in the conf files and cant see.

thanks . . .

---

### Post by solidblu on 2009-09-19
[http://www-uxsup.csx.cam.ac.uk/~jw35/courses/apache/html/x1670.htm](http://www-uxsup.csx.cam.ac.uk/~jw35/courses/apache/html/x1670.htm)


If you read this link it'll show you an example but what you need to do is edit

/etc/logrotate.d/apache2  and add a size=  line under /var/log/apache2/* 

hope this helps

---

### Post by falconindy on 2009-09-19
By default, Apache logs roll over to a new log each week and the old log is gzipped. This is done by logrotate. Settings can be found in /etc/logrotate.d/apache2.

edit: bah, beaten to the punch. Keep in mind that logrotate is triggered when ANY of the conditions are true. In exchange for adding the size= condition, you'll need to get rid of the 'weekly' and probably 'rotate 52' lines.

---

