---
title: "anacron jobs executing twice a day, no weekly jobs"
date: 2012-02-28
forum: General Help
---

### Post by sapeurcamembert on 2012-02-28
I am running Ubuntu 11.04 (fresh install) and I am using rsnaphot to take incremental backups. I am using my desktop time to time and decided to let the system takes the backup for me.

Stangely enough rsnapshot as started by anacon is executing twice a day and weekly never been executed...

I am dealing with the same problem for a couple of weeks and decide to ask for help.

**[COLOR="blue"]First anacron as supplied by 11.04 install (not changed)[/COLOR]**

# /etc/cron.d/anacron: crontab entries for the anacron package

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

#30 7    * * *   root	test -x /etc/init.d/anacron && /usr/sbin/invoke-rc.d anacron start >/dev/null
30 7    * * *   root	start -q anacron || 

**[COLOR="blue"]Next crontab table (empty) everything is commented out[/COLOR]**

 /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user	command
#17 *	* * *	root    cd / && run-parts --report /etc/cron.hourly
#25 6	* * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
#47 6	* * 7	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
#52 6	1 * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )

**[COLOR="Blue"]Next anacrontab as set up[/COLOR]**

# /etc/anacrontab: configuration file for anacron

# See anacron(8) and anacrontab(5) for details.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# These replace cron's entries
1	5	cron.daily	 nice run-parts --report /etc/cron.daily
7	10	cron.weekly	 nice run-parts --report /etc/cron.weekly
1	120	mysnap.daily	/home/am/bin/mysnap.sh -v daily
7	180	mysnap.weekly	/home/am/bin/mysnap.sh -v weekly
30	240	mysnap.monthly	/home/am/bin/mysnap.sh	-v monthly
@monthly	15	cron.monthly nice run-parts --report /etc/cron.monthly

**[COLOR="Blue"]Next mysnap.sh script (executed as root)[/COLOR]**

#!/bin/sh
# An Easy command to use the rsnapshot command. 

period="daily"

if [ $# -eq 1 ] ; then
       period=$1
fi

echo $period

/usr/bin/rsnapshot -v $period >> /var/log/rsnapshot

du -s -h /media/7444bkup -h >> /var/log/rsnapshot
ls -al /media/7444bkup/.snapshots/ >> /var/log/rsnapshot 

# Send log to email

cat /var/log/rsnapshot | ssmtp sapeurcamembert@myemail

# Reset log after weekly processing

if [ $period -eq "weekly" } ; then
	cat /dev/null > /var/log/rsnapshot
fi

The file /var/spool/anacron/cron.daily is updated with the time stamp (date only as usual) 20120228 as today

The file /var/log/rsnapshot is never reset....and the weekly period is never executed....

Any help will be appreciated.:P

---

