---
title: "cron not running?"
date: 2011-06-01
forum: General Help
---

### Post by sgardne on 2011-06-01
I have the following set up in my crontab:

```
# crontab -l
# m h  dom mon dow   command
*/5 * * * * /usr/bin/perl /usr/local/bin/perl/managed_arp_data.pl >> /var/log/arpdb.log
*/5 * * * * /usr/bin/perl /usr/local/bin/perl/infoblox_fixed_sync.pl >> /var/log/crossref.log
00 23 * * * /usr/bin/perl /usr/local/bin/perl/infoblox_host_sync.pl >> /var/log/host_sync.log
0 * * * * /usr/bin/perl /usr/local/bin/perl/infoblox_excl_sync.pl >> /var/log/excl_sync.log
```

None of these jobs is apparently running, however they did run on the 31st (yesterday), but not on the 30th or any other day during the last 10 days that I have logs for. I think I've set cron to run at log level 1, but I don't know where that log goes, I don't see anything like /var/log/cron

So, couple questions:

* If I do something like "sudo -s" to get a root prompt and then do a "crontab -e", which user does that crontab get executed as?

* Where should I look for cron logs?

* Anyone know why a job would run on the 31st, but not any other day?

---

### Post by simon_w on 2011-06-01
fella you've been super unlucky, I reckon, and just happened to set your `crontab` up the day before one of Ubuntu's bigger ****-ups of recent times [https://bugs.launchpad.net/ubuntu/natty/+source/pam/+bug/790538]("https://bugs.launchpad.net/ubuntu/natty/+source/pam/+bug/790538")

perform a full `apt-get update && apt-get upgrade` and/or restart the cron-daemon, and you should be good to go :)

---

