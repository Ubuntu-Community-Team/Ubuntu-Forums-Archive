---
title: "Complete sys freeze - help with logs please."
date: 2009-07-27
forum: General Help
---

### Post by musther on 2009-07-27
I've recently got a new computer, and am all of a sudden experiencing complete system freezes.  Sometimes I'm browsing the web, sometimes I'm not even at the machine, no input, screen frozen in whatever state it was at the time.  Attached is a file containing the relevant sections of all of my log files.  The freeze in question occured at about 15:2X.  One interesting thing I can see (although this could be rubbish) is in auth.log, the repeated opening of root sessions by cron from uid=0.  Well running crontab -l as root shows no cron jobs.  

I appreciate that most people will scream 'hardware issue', but I've successfully run the machine with memtest86 for many hours with no incident, I've also used the machine in windows, and until recently, with no problem in Ubuntu (seems to be a new issue).  I've also looked at the temperature of the board and CPU, and it seems absolutely fine.

So, now I'm in your hands!  Thanks.

---

