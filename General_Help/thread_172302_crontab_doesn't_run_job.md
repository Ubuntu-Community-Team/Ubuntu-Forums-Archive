---
title: "crontab doesn't run job"
date: 2006-05-08
forum: General Help
---

### Post by sojourner9 on 2006-05-08
Having a bit of a problem getting cron to run the jobs in my crontab file.

From "crontab -l", its the last job I'm worried about right now.  Want it to run every 5 minutes.  And, until I'm sure it working right - want it to ship returns and errors into that error.txt file.

```

## USE BIN/SH TO RUN COMMANDS
SHELL=bin/sh
#
#
# ALL ERRORS SHOULD BE PIPED TO THE SAME ERROR FILE
#
# RUN THE SCRIPT TO GRAB THE PORT CONFIGS EVERY DAY AT 0400
0 4 * * *       /www/cgi-bin/port-count.pl 2>/home/mfountain/error.txt
#
# THEN RUN THE SCRIPT TO EMAIL THE RESULTS AT 0405
5 4 * * *       /www/cgi-bin/port-count-email.pl 2>/home/mfountain/error.txt
#
# RUN THE SCRIPT TO INDEX THE WEB PAGES EVERY MORNING AT 0600
0 6 * * *       /www/search/indexing/index.sh 2>/home/mfountain/error.txt
#
# RUN THE SCRIPT TO TEST EPR SERVERS FOR BANDWIDTH
0,5,10,15,20,25,30,35,40,45,50,55 * * * * /www/cgi-bin/rrd_snmp.pl >/home/mfountain/error.txt 2>&1

```


It looks like it is trying to run.  Here is my syslog file:

```

May  8 10:35:02 NetEngLinux /USR/SBIN/CRON[11681]: (mfountain) CMD (/www/cgi-bin/rrd_snmp.pl >/home/mfountain/error.txt 2>&1)

```

But, the error.txt file is not updated, and the files that the perl script are supposed to update are not updated.

When I run that command manually, 
"/www/cgi-bin/rrd_snmp.pl >/home/mfountain/error.txt 2>&1"
 everything works fine.  error.txt is updated and the rrd file is updated by the perl script.


Any idea why it doesn't seem to be working from cron?

---

### Post by exosyst on 2006-05-08
It's not something as simple as the lack of a space between your redirection operator?

/www/cgi-bin/rrd_snmp.pl** > **/home/mfountain/error.txt

---

### Post by sojourner9 on 2006-05-08
doesn't seem to matter either way.  Examples I've seen didn't have a space, but I tried it.  The line is now this:

```

# RUN THE SCRIPT TO TEST EPR SERVERS FOR BANDWIDTH
0,5,10,15,20,25,30,35,40,45,50,55 * * * * /www/cgi-bin/rrd_snmp.pl > /home/mfountain/error.txt

```

Still see it like its running in syslog, but no updates in the .txt file unless I enter that command in manually

---

### Post by sojourner9 on 2006-05-09
Any other ideas on tihs one?

---

