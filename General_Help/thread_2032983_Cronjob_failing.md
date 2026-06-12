---
title: "Cronjob failing"
date: 2012-07-25
forum: General Help
---

### Post by butleredwin on 2012-07-25
Hi There

Ok so I would like to find out why my cronjobs are failing. I see the following in the syslog but cant find any good reason when I search for the problem on-line.

There error messages are as follows:


Jul 25 06:45:01 userpc CRON[4475]: (root) CMD (getmail -r /home/martin/.getmail/getmail.webmail)
Jul 25 06:45:01 userpc CRON[4476]: (root) CMD (getmail -r /home/jane/.getmail/getmail.webmail)
Jul 25 06:45:01 userpc CRON[4477]: (root) CMD (getmail -r /home/edwin/.getmail/getmail.webmail)
Jul 25 06:45:01 userpc CRON[4478]: (root) CMD (getmail -r /home/jacobus/.getmail/getmail.webmail)
Jul 25 06:45:01 userpc CRON[4483]: (root) CMD (getmail -r /home/waldo/.getmail/getmail.webmail)
Jul 25 06:45:01 userpc CRON[4484]: (root) CMD (getmail -r /home/kobus/.getmail/getmail.webmail)
Jul 25 06:45:01 userpc CRON[4472]: (CRON) info (No MTA installed, discarding output)
Jul 25 06:45:01 userpc CRON[4469]: (CRON) info (No MTA installed, discarding output)
Jul 25 06:45:01 userpc CRON[4470]: (CRON) info (No MTA installed, discarding output)
Jul 25 06:45:01 userpc CRON[4473]: (CRON) info (No MTA installed, discarding output)
Jul 25 06:45:01 userpc CRON[4471]: (CRON) info (No MTA installed, discarding output)
Jul 25 06:45:01 userpc CRON[4474]: (CRON) info (No MTA installed, discarding output)


So this is the problem '**(CRON) info (No MTA installed, discarding output)**'

And my crontab looks like this:

* 6 * * * getmail -r /home/edwin/.getmail/getmail.webmail
* 6 * * * getmail -r /home/waldo/.getmail/getmail.webmail
* 6 * * * getmail -r /home/kobus/.getmail/getmail.webmail
* 6 * * * getmail -r /home/jacobus/.getmail/getmail.webmail
* 6 * * * getmail -r /home/jane/.getmail/getmail.webmail
* 6 * * * getmail -r /home/martin/.getmail/getmail.webmail

I suspect the output of the log is too much for syslog.

any suggestions?

---

### Post by butleredwin on 2012-07-25
Ok found the problem

Seems like Ubuntu does not come with this standard but you need to have a mailito installed.

sudo apt-get install mailutils

But once I has this I could get the error message form the mail.

Error: Default config/data dir "/root/.getmail/" does not exist - create or specify alternate directory with --getmaildir option

So had to run the cronjob as individual users and not as root.:P

and for those who want to write their cronjob logs to /var/log/cron.log follow the following that I got from askubuntu:

You can create a cron.log file to contain just the CRON entries that show up in syslog. Note that CRON jobs will still show up in syslog if you follow the following directions.

Open the file

/etc/rsyslog.d/50-default.conf
Find the line that starts with:

#cron.*
uncomment that line, save the file, and restart rsyslog:

sudo service rsyslog restart
You should now see a cron log file here:

/var/log/cron.log
Cron activity will now be logged to this file (in addition to syslog).

Note that in cron.log you will see entries for when cron ran scripts in /etc/cron.hourly, cron.daily, etc. - e.g. something like:

Apr 12 14:17:01 cd CRON[14368]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
However, you will not see more information about what scripts were actually ran inside /etc/cron.daily or /etc/cron.hourly, unless those scripts direct output to the cron.log (or perhaps to some other log file).

If you want to verify if a crontab is running and not have to search for it in cron.log or syslog, create a crontab that redirects output to a log file of your choice - something like:

01 14 * * * /home/joe/myscript >> /home/log/myscript.log 2>&1
This will redirect all standard output and errors that may be produced by the script that is run to the log file specified.

---

