---
title: "short high load, but unable to track the process causing it"
date: 2009-10-20
forum: General Help
---

### Post by Nstuff on 2009-10-20
Hello,

I got a problem with an Ubuntu server (8.10) which is running an apache/mysql/etc (sort of hosting server). Every random period the server gets a high load by an process. This can be during the day, during the night, basically anytime. Sometimes its not there for a few days and sometimes it gets an high load twice a day.

The problem is basically I can't figure out what process this may be causing. I monitor the server with Nagios, and everytime I get a load message the load is already dropping. And the process that caused it is gone. Is there a program that I can load that monitors its own load and when certain 'load' is reached it captures a process-list and puts it in a logfile, or mail it to me? So I might be figuring out what process is the cause of this load increase.

Thanks for the help.
Regards
Nstuff

---

### Post by P4man on 2009-10-20
Could it be mlocate (or slocate?) in /etc/cron.daily ? It runs every day by default and indexes your harddrive. You could move it /etc/cron.weekly to test, though I suspect someone will be able to provide an actual answer to your question.

---

### Post by Nstuff on 2009-10-20
Thanks for the quick response. I moved mlocate to the weekly cron, but I doubt this is the cause. For an idea about the times and the load problems:

Date/Time: Sat Oct 17 14:11:52 CEST 2009
Additional Info:
WARNING LOAD: 3.87, 4.80, 2.14

Than a few days nothing, although it could be that it happens every day, but that the nagios monitoring just missed it... (interval is 2 minutes) and than twice today:

Date/Time: Tue Oct 20 00:46:09 CEST 2009
Additional Info:
WARNING LOAD: 3.05, 5.48, 2.88

Date/Time: Tue Oct 20 15:18:24 CEST 2009
Additional Info:
WARNING LOAD: 2.55, 6.65, 3.89

---

