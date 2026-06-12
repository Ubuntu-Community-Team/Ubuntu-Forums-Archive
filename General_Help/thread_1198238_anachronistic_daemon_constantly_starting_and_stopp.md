---
title: "anachronistic daemon constantly starting and stopping"
date: 2009-06-27
forum: General Help
---

### Post by genjix on 2009-06-27
hello,

when i shut down X on one of my computers I noticed that the anachron daemon keeps starting and stopping constantly every 2 secs or so.

Is this normal?

Thanks.

---

### Post by geirha on 2009-06-27
No, it should only run about once a day. What does your /etc/crontab look like?

---

### Post by genjix on 2009-07-01
> # /etc/crontab: system-wide crontab
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
#


seems kind of normal.

---

### Post by genjix on 2009-07-01
also this laptop runs veeeerrry slow eventhough it shouldnt.

it has an intel gfx card so i thought it could be [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582) ... but following this guide made it even slower.

so now i think it could be something related to this cron starting and stopping a lot.

---

### Post by geirha on 2009-07-01
Nothing out of the ordinary in "sudo crontab -l" either?

Could you post a sample of the log-messages you are seeing?

---

