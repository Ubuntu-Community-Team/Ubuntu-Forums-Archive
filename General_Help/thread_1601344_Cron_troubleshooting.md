---
title: "Cron troubleshooting"
date: 2010-10-20
forum: General Help
---

### Post by laughlin.bill on 2010-10-20
Hi -

I need some advice on how to troubleshoot some cron jobs which are not completing.  I have several bash scripts which I have scheduled to start automatically wtih cron.  Sometimes they complete, other times they randomly stop execution somewhere in the middle of the script.  I have tested these scripts standalone (i.e. without the cron scheduler) and they always run to the end.

I have checked the syslog for some sort of event that might have caused them to shutdown, but I cannot find anything.

Is there any way to get a more detailed cron log?  My bash scripts log every action they take with a timestamp, however I have not captured any system messages; Any suggestions on how I can better log my bash scripts to figure out what is going on?

Thanks for any advice

---

### Post by DaithiF on 2010-10-20
Hi,
for the symptom you describe of cron jobs stopping somewhere in the middle of the script, it sounds like the issue described here:
[http://wwww.ubuntuforums.org/showthread.php?p=9989923](http://wwww.ubuntuforums.org/showthread.php?p=9989923)

---

### Post by laughlin.bill on 2010-10-20
That's it!  Thanks for the quick reply.

---

