---
title: "cron - trivial help needed."
date: 2011-03-26
forum: General Help
---

### Post by Trunkles on 2011-03-26
Hi folks.

I'm running Meerkat server. I inserted the following line into /etc/crontab

*/10 *    * * *   root  /usr/bin/woottime > /home/simon/wootlog

If I run that command from the command line it behaves impeccably but, cron doesn't seem to run it at all!

So, please, what have I done wrong? Or not done? Or whatever!

Thankies.

Simon.

---

### Post by Krytarik on 2011-03-27
May that be the case?
> When adding a new entry to a blank crontab, forgetting to add a newline at the end is a common source for the job not running. If the last line in the crontab does not end with a newline, no errors will be reported at edit or runtime, but that line will never run.
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

### Post by Trunkles on 2011-03-27
Thankies. That wasn't the problem though.

I was editing /etc/crontab. However, when I tried a crontab -e I found the entry wasn't in that file! it is now and behaves perfectly.

I do get the feeling that the various crontabs are confusing. Is /etc/crontab ever actually read? i've done /etc/init.d/cron restart several times but a crontab -l doesn't show what I expect. Ver confusing. :(

Thanks for your help though.

Simon.

---

### Post by Krytarik on 2011-03-27
- "/etc/crontab" is the system/root cron file.

- "crontab -e" (without 'sudo') allows the modification of the user's cron file

There are some markable differences between both setups, like described in the guide I mentioned.
And the way you had it should actually also work.

---

