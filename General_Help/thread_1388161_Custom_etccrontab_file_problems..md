---
title: "Custom /etc/crontab file problems."
date: 2010-01-22
forum: General Help
---

### Post by JetSirus on 2010-01-22
First, this system is a public access desktop system in a hotel lobby.  I need to make a very specific set of jobs and have them run system wide at specific times, no matter the user account.  So I decided to use /etc/crontab.  Here is the contents of my /etc/crontab file.

```

# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user	command
00 1    * * *   root    zenity --info --text "System beginning update cycle.  Internet service may slow temporarily."
01 1    * * *   root    apt-get update
05 1    * * *   root    apt-get upgrade
30 1    * * *   root    zenity --info --text "System rebooting in 15 minutes.  Please save any work before then."
40 1    * * *   root    zenity --info --text "System rebooting in 5 minutes.  Please save any work now."
44 1    * * *   root    zenity --info --text "System rebooting in 1 minute.  Please save any work now."
45 1    * * *   root    reboot
17 *	* * *	root    cd / && run-parts --report /etc/cron.hourly
25 6	* * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6	* * 7	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6	1 * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
#


```

Yet none of the extra stuff runs.  In fact, unless I log into the main admin account, the contents of the /etc/crontab file are the defaults seen in most anacron setups.  Any tips on what I am doing wrong?

---

### Post by JetSirus on 2010-01-23
Daily bump.

---

### Post by happyhamster on 2010-01-23
To be able to run graphical stuff from crontab, you'll have to set the DISPLAY environment variable, and you'll probably have to make sure that users have access to the X server, by running xhost. For example:

```

00 1    * * *   root    DISPLAY=":0.0" /usr/bin/zenity --info --text "Hello"

```

- And then run (when logged in as that user):

xhost local:

- To find the current DISPLAY value:

env | grep display -i

- Go here for more info:
[http://www.leidinger.net/X/xhost.html](http://www.leidinger.net/X/xhost.html)

- edit: and here:
[http://www.tuxradar.com/answers/605](http://www.tuxradar.com/answers/605)

Good luck.

---

### Post by JetSirus on 2010-01-23
Thanks, I managed to get it working that way.  Took some doing.

---

