---
title: "cron job not running"
date: 2010-05-26
forum: General Help
---

### Post by mjo1337 on 2010-05-26
HI,

I'm trying to configure a cronjob to WGET something at a set time

For testing purposes I've tried setting this to ever 1 minute just to see if it works

I have tried various different configs:

1 * * * * root wget URL
*/1 * * * * wget URL
1 * * * * wget URL

crontab -e   <-- tried putting it in here
sudo crontab -e <-- tried putting it in here
\etc\crontab <-- tried putting it in here

but it never works. It's a standard install of Ubuntu, I haven't changed anything so I'm a bit confused as to why it's not working.

Any ideas?

Cheers

---

