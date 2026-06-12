---
title: "set the time for updatedb.mlocate to run"
date: 2010-07-23
forum: General Help
---

### Post by TeAmigo on 2010-07-23
I am trying to set the time that updatedb.mlocate runs. My understanding is that it is run daily, and the time the daily cron jobs are run ins controlled via /etc/crontab. Obviously my understanding is incomplete. I've change /etc/crontab to run the dailes at 4 in the afternoon but updatedb.mlocate still seems to crank away at 6am. Here is my current /etc/crontab:

# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user    command
17 *    * * *    root    cd / && run-parts --report /etc/cron.hourly
25 16    * * *    root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 16    * * 7    root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 16    1 * *    root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
#

Could someone tell me what I need to do to get updatedb.mlocate to NOT run at 6am, but rather at 4pm? Thank you for any help.

---

