---
title: "Help Track Cron Job"
date: 2012-03-11
forum: General Help
---

### Post by xathras1982 on 2012-03-11
Hi,
 
I have checked all the cron folders and crontab and find no entry, but i see these in my logs every 30 minutes. Is there anyway to track this down?
 
Mar 11 13:30:01 ubuntu CRON[29552]: (root) CMD (/usr/lib/cgi-bin/awstats.pl -config=domain.info -update &gt; /dev/null)
Mar 11 13:30:01 ubuntu CRON[29551]: (CRON) error (grandchild #29552 failed with exit status 126)

 
Regards
Wayne

---

### Post by xathras1982 on 2012-03-11
Ignore me. Such a damn @ss.. Missed looking at /etc/crontab when i did everything else!

---

