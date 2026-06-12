---
title: "trouble installing php5-gd"
date: 2010-09-21
forum: General Help
---

### Post by windsurflove on 2010-09-21
I am having trouble getting php5-gd to work on lucid lynx.  

A little history:
At some point I downgraded php5.3 to php5.2.10.  
Then I upgraded back to php5.3, did apt-get install php5-gd, but the library doesn't work.  
I don't see it in phpinfo (see my phpinfo attached)

A little troubleshooting:
1. I can see gd.so in /usr/lib/php5/20090626+lfs/.   So the extension is present.
2. I can see  /etc/php5/apache2/conf.d/gd.ini, in it there is the line extension=php.so.  So the instruction to load the extension is there.

I have tried the following:
1. apt-get purge php5-gd, then apt-get install php5-gd, then restart apache.  Didn't work
2. I have tried the same using Synaptic Package manager.  Still didn't work.

Please help me!!!

---

