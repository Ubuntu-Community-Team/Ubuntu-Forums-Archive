---
title: "cron job to send email reminders?"
date: 2006-04-01
forum: General Help
---

### Post by chusome on 2006-04-01
I'm looking for a how to to setup a cronjob to send email reminders. Specifically I'd like to not have to use the mailx/postfix, but instead use my isp's send mail server.

Anyone have info on this?
Can it be done?

---

### Post by chusome on 2006-04-06
anyone?

---

### Post by rjcroy on 2006-04-06
I think have been doing kinda what you are talking about. But I don't know how you could do it without using a MTA, even if you are just pushing the email to your ISP's send mail server.

I have a debian box that backs up my files to another computer on the network every morning at 5am and then emails me a report on whether the back up was successful.

The MTA is exim, and is configured to route all outgoing mail to the local send mail server.
quote from exim.conf:
```
# This router routes to remote hosts over SMTP using a DNS lookup with
# default options.

internet:
           driver = domainlist
           transport = remote_smtp
           route_list = * mail.mydomain.com bydns_a
```

Then the backup script can just inject an email into the MTA
```
#!/bin/sh
...
/usr/sbin/sendmail -i -t -f rjcroy@mydomain.com < mail.txt

```

But that's probably not the elegant solution you want.

---

