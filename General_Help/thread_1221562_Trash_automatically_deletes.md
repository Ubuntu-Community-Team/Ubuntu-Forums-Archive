---
title: "Trash automatically deletes"
date: 2009-07-24
forum: General Help
---

### Post by Nburnes on 2009-07-24
As my title states my trash automatically deletes anything I put into it. I checked under preferences in Nautilus and I have checked under Trash that it should ask before emptying or deleting files.

How could I go about making this not happen?

---

### Post by Elep.Repu on 2009-07-24
Woh, that's pretty strange.
Check: 
/etc/[I]crontab

[/I]Anything out of the ordinary?

---

### Post by Nburnes on 2009-07-24
I have no idea what this means

```
SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user    command
17 *    * * *    root    cd / && run-parts --report /etc/cron.hourly
25 6    * * *    root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6    * * 7    root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6    1 * *    root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
#
```Edit: I did sudo gedit /etc/crontab if that is alright?
Edit 2: Updated to 9.10 Alpha 3 and now it works just fine?

---

