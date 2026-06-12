---
title: "stuck with cron basics"
date: 2010-08-13
forum: General Help
---

### Post by jonnybignote on 2010-08-13
Hi all

running 9.10 x64

My scripts in cron.daily are not running correctly.

I am not using Anacron but waking my computer every night to run cron jobs - does that mean I should remove the anacron references from the cron lines or can they be left as is?

This is my current file (note, I've commented out the originals)

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
#09 04  * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
09 04   * * *   root    cd / && run-parts --report /etc/cron.daily
#04 04  * * 7   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
04 04   * * 7   root    cd / && run-parts --report /etc/cron.weekly
#06 04  1 * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
06 04   1 * *   root    cd / && run-parts --report /etc/cron.monthly
```




my cron logging is messed up and all I get is one line saying its started (cron.daily etc) without any individual script details.  So figuring out what is going wrong is difficult

if I type into terminal 

```
run-parts --report /etc/cron.daily

```

the scripts will run but they have all kinds of permissions errors relating to creating files or directories so I have problems there also....

I'm starting to lose track of this system as it seems to have inherited various oddities and corruptions over the last 2 years, due in great part I imagine to my haphazard knowledge of linux.

This machine running my mythtv so it would be nice if I didn't have to reformat and start again but many of the scripts running are important and I need to figure this out.

Any help will be much much appreciated

Thanks

---

