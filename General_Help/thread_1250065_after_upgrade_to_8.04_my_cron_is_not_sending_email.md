---
title: "after upgrade to 8.04 my cron is not sending emails"
date: 2009-08-26
forum: General Help
---

### Post by c01e on 2009-08-26
Hi,

Last night I upgraded all my servers from 7.10 to 8.04 and now I'm not getting cron emails.

My cron is working. Tested via adding * * * * * date >> /root/test.log

However I'm not getting emails? I only upgraded - I didn't change any config (only replaced some config files with the maintainers version). So /etc/aliases still has root set to my username and my ~/.forward file has my email address. 

FYI: I'm using exim as my IMAP/SMTP server and I am getting emails from it for other ****. Just not cron emails.

Any ideas?

---

### Post by danwood76 on 2009-08-26
Upgrades can cause issues between configurations of different versions.

I would check your cron configs and verify they will work for the installed versions.

---

### Post by c01e on 2009-08-26
I'm aware of that...

Anyway, fixed it. Silly me forgot up change my smarthost in exim, as I also changed ISP's yesterday.

---

