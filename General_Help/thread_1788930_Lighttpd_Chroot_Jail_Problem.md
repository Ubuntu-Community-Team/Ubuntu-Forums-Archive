---
title: "Lighttpd Chroot Jail Problem"
date: 2011-06-23
forum: General Help
---

### Post by Faks on 2011-06-23
Hi everybody it's been a while since my last post here but seems problems know how to make me suffer and ask for help sow let's cut to the chase !
Problems is very hard to locate and resolve i made lighttpd php5-cgi server with chroot it works but not like it should many modules or sow called extensions refuse to load in most funny thing is that all folders all dir are copied and checked it's been long more than 72h and still i am trying to resolve all problems
visit this link to see [php info ]("http://net2ftp.hostings.flush.ws/zone.php") 
odd some extensions seems loads in or they are default not sure but since them working why all other not working ?

Target of Thread is To Resolve Bug or Mistake if such exist !

**Small Off topic but still is related to case !**
Used following tutorial [http://www.cyberciti.biz/tips/howto-setup-lighttpd-php-mysql-chrooted-jail.html](http://www.cyberciti.biz/tips/howto-setup-lighttpd-php-mysql-chrooted-jail.html) most of information is out of date but if know how to adapt it then problems are far more smaller sow i did but even sow still i have most hard time i think community should come together once again and write a proper tutorial for chroot for all servers or somebody should take this role .

---

### Post by Faks on 2011-06-23
[LEFT]seems problems were related to extensions but i still encounter problems with mysql i hope to setup all clean then clean out crap and then write a proper tutorial or publish correct folder order to make right chroot :guitar: because i get tired of old tutorials witch mostly are wrong or are too out of date and they can screw you really bad !
[/LEFT]

---

### Post by justinperkins1@gmail.com on 2011-06-28
I also had some issues with this howto but when you combined the ubuntu instructions with the original article and don't use the lighttpd.conf that gets installed with apt-get install lighttpd, but the example one that's linked in the original article, things work much better. Between the two articles there are differences and no steps can be omitted even though you need both articles to discover all required steps.

*edit*

here's the link that fixed my settings: [http://www.cyberciti.biz/files/lighttpd/debian-lighttpd.conf.txt](http://www.cyberciti.biz/files/lighttpd/debian-lighttpd.conf.txt)

---

