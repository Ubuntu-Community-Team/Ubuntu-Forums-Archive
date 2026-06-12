---
title: "/etc/crontab none loading"
date: 2010-11-02
forum: General Help
---

### Post by craigp on 2010-11-02
they were all working and then after restarting none of the jobs in /etc/crontab are working. the onlything that i changed was restarting it.


```
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user  command
17 *    * * *   root    cd / && run-parts --report /etc/cron.hourly
25 6    * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6    * * 7   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6    1 * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )


# Backup all MySQL Databases
0 2 * * 0 root /home/public_html/db-backup/weeklydb.sh


# Update Chart
0 5 * * * root php /home/public_html/www/data/UpdateHistoric.php
10 5 * * * root php /home/www/public_html/www/data/MySQL.php


#backup entire web files - Every sunday at 1am
0 1 * * 0 root /home/public_html/admin/backup/BackupFiles.sh
```

any help would be much appreciated

---

### Post by matt_symes on 2010-11-02
Hi

Is cron running

Open a terminal and type

sudo /etc/init.d/cron status

Kind regards

---

### Post by craigp on 2010-11-02
thanks for the quick response.. i run that command and it just moves down to the next line.

i tried:
sudo /etc/init.d/cron start

then it just moves down to the next line

then i try this again:
sudo /etc/init.d/cron status

and the same thing happens

---

### Post by matt_symes on 2010-11-02
Hi

Hmm. That's a bit strange. You could try uninstalling and reinstalling cron. I have never had a problem with cron, so i might not be the best person to help.

However, if you can find no other solution you could try

sudo apt-get remove cron
sudo apt-get install cron

and see if that fixes it.
Unless i am going blind (that is possible) the file looks alright.

Kind regards

---

### Post by craigp on 2010-11-02
> **matt_symes said:**
> Hi

Hmm. That's a bit strange. You could try uninstalling and reinstalling cron. I have never had a problem with cron, so i might not be the best person to help.

However, if you can find no other solution you could try

sudo apt-get remove cron
sudo apt-get install cron

and see if that fixes it.
Unless i am going blind (that is possible) the file looks alright.

Kind regards

did that and it appears to be working so far.. thanks man

---

### Post by RedScourge on 2011-05-03
I am posting this here incase someone coming here runs into the issue that I did, which took me days to figure out!

If you are using scripts named something like script.sh and they are in  folders such as /etc/cron.hourly, make sure you modify your /etc/crontab  (or /etc/anacrontab) file or they will not run!!!

  For example, in /etc/crontab:
   
1 * * * * root cd /tmp && run-parts --report /etc/cron.daily
   
Change to:
   
   1 * * * * root cd /tmp && run-parts --regex='(.*)' --report /etc/cron.daily


Unlike some other systems like RedHat/Fedora/etc, run-parts under Debian  or Ubuntu systems will ignore files with dots or most other characters  in their name, meaning some or all of your scripts in run-parts folders  such as /etc/cron.daily will not be run. For example  /etc/cron.daily/backup.sh will never be run with the default way that  /etc/crontab is set up.
  
  From man cron:
  
  "Files must conform to the same naming convention as used by  run-parts(8): they must consist solely of upper- and lower-case letters,  digits, underscores, and hyphens. If the -l option  is specified, then  they must conform to the LSB namespace specification, exactly as in the  --lsbsysinit option in run-parts."

---

