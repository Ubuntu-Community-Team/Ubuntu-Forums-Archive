---
title: "Using /etc/crontab to force chown and chmod in specific directory"
date: 2011-02-09
forum: General Help
---

### Post by effenberg0x0 on 2011-02-09
I need to actively make sure some files, in a specific directory, are chmod 750 and owned by transmission:media-daemons. Other users will save to this directory, with other permissions and UID/GID but I must make sureto reinforce this default.

So I have this on my /etc/crontab:

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
1  *    * * *   root    chmod 750 -R /media/raid01/public/daemons/transmission-daemon/watch && chown transmission:media-daemons -R /media/raid01/public/daemons/transmission-daemon/watch

#

```

It doesn't work. 

Can anyone give me a tip?

Thanks.

---

### Post by anglican on 2011-02-09
> **effenberg0x0 said:**
> I need to actively make sure some files, in a specific directory, are chmod 750 and owned by transmission:media-daemons. Other users will save to this directory, with other permissions and UID/GID but I must make sureto reinforce this default.

So I have this on my /etc/crontab:

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
1  *    * * *   root    chmod 750 -R /media/raid01/public/daemons/transmission-daemon/watch && chown transmission:media-daemons -R /media/raid01/public/daemons/transmission-daemon/watch

#

```

It doesn't work. 

Can anyone give me a tip?

Thanks.cron runs silently when all is well, otherwise there is output to the users mail. So to diagnose problems you need to look at root's mail:
```
sudo bash
mail
```one of the most frequent problems with cron is caused by failing to give the full path to a command i.e. use /bin/chmod and /bin/chown. The other most common problem is incorrectly specifying the time at which you want things to happen. "1  *    * * *" means "do this at one minute past the hour - every hour" i.e. once per hour, is this what you want?

H

---

