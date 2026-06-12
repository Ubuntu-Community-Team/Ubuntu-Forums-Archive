---
title: "Crontab / ntp.ubuntu.com Not Updating Time"
date: 2011-09-09
forum: General Help
---

### Post by mkhaytman on 2011-09-09
I have got cron set up to update the time on my server hourly. Today I took at look and found my time was 19 minutes off, with the last logged update being sometime in April!

```
root@marvin:/var/log# crontab -l
# m h dom mon dow   command
0 * * * * /usr/local/bin/cron/time.sh
```

```
root@marvin:/var/log# cat /usr/local/bin/cron/time.sh
#!/bin/bash
###########
ntpdate ntp.ubuntu.com>/var/log/cronlog/run/date_`date +%Y.%m.%d`
```
```

root@marvin:/usr/local/bin/cron# cat /var/log/syslog | grep time.sh
Sep 9 07:00:01 marvin CRON[10535]: (root) CMD (/usr/local/bin/cron/time.sh)
Sep 9 08:00:01 marvin CRON[18681]: (root) CMD (/usr/local/bin/cron/time.sh)
Sep 9 09:00:01 marvin CRON[26823]: (root) CMD (/usr/local/bin/cron/time.sh)
Sep 9 10:00:01 marvin CRON[3257]: (root) CMD (/usr/local/bin/cron/time.sh)
Sep 9 11:00:01 marvin CRON[11355]: (root) CMD (/usr/local/bin/cron/time.sh)
Sep 9 12:00:01 marvin CRON[19205]: (root) CMD (/usr/local/bin/cron/time.sh)
```



I'm not sure what the issue could be, any tips?

---

### Post by mkhaytman on 2011-09-12
Bump. Any help at all would be appreciated. Take a stab at it even if you don't know for sure, you might get me on the right path to figuring this out.

---

### Post by gmargo on 2011-09-12
You captured the output from **ntpdate**.  What was it?  Did it even run?

Was there anything more in the syslog file for each run?  That simple grep won't show it.  If cron itself is having an error it will try to email that to you.  The log will tell if cron tried to send anything.

**ntpdate** can take multiple servers on the command line; you're not limited to just one.

However, I would (and do) just use **ntp**, syncing to multiple time servers.

---

### Post by mkhaytman on 2011-09-12
> **gmargo said:**
> You captured the output from **ntpdate**.  What was it?  Did it even run?


No, it didn't run. The logs are empty. 

```
root@marvin:~# cat /var/log/syslog | grep 'Sep 12 13:00:0'
Sep 12 13:00:01 marvin CRON[32627]: (root) CMD (/usr/local/bin/cron/time.sh)
Sep 12 13:00:01 marvin postfix/pickup[13543]: 2499C94060B: uid=0 from=<root>
Sep 12 13:00:01 marvin postfix/cleanup[32636]: 2499C94060B: message-id=<20110912170001.2499C94060B@marvin.#####.net>
Sep 12 13:00:01 marvin postfix/qmgr[21755]: 2499C94060B: from=<root@marvin.#####.net>, size=589, nrcpt=1 (queue active)
Sep 12 13:00:01 marvin postfix/local[32641]: 2499C94060B: to=<root@marvin.#####.net>, orig_to=<root>, relay=local, delay=0.2, delays=0.13/0/0/0.06, dsn=2.0.0, status=sent (delivered to mailbox)
Sep 12 13:00:01 marvin postfix/qmgr[21755]: 2499C94060B: removed
```

---

### Post by gmargo on 2011-09-12
> **mkhaytman said:**
> No, it didn't run. The logs are empty. 

Sep 12 13:00:01 marvin postfix/local[32641]: ... to=<root@marvin.#####.net>   ...  [COLOR=Red]status=sent (delivered to mailbox)[/COLOR]



So cron sent email to the root account.  Check **/var/mail/root** for the message(s).

(I would update **/etc/aliases** so that "root" and "postmaster" email goes to your account.)

---

### Post by linux2001 on 2011-09-13
Try to execute this script in shell and see the output
or try
```
root@marvin:/var/log# crontab -l
# m h dom mon dow   command
0 * * * * bash /usr/local/bin/cron/time.sh
```

---

### Post by SeijiSensei on 2011-09-13
> **gmargo said:**
> However, I would (and do) just use **ntp**, syncing to multiple time servers.

+1 

There's no need to run ntpdate from cron.  Just use the ntpd daemon instead. It will automatically check with the servers periodically and keep your clock correct.  

```
sudo apt-get install ntp
```

If you have custom servers you wish to use instead of the default, ntp.ubuntu.com, add them to /etc/ntp.conf, then restart ntpd with "sudo service ntp restart".

---

### Post by mkhaytman on 2011-09-13
Solved! Thank you for all your help!

```
/usr/local/bin/cron/time.sh: line 3: ntpdate: command not found
```it was caused because the cron PATH variable didn't include /usr/sbin/

we fixed it by changing the time.sh script:
```
#!/bin/bash
###########
/usr/sbin/ntpdate ntp.ubuntu.com>/var/log/cronlog/run/date_`date +%Y.%m.%d`

```

---

