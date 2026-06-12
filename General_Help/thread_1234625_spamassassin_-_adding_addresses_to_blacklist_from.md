---
title: "spamassassin - adding addresses to blacklist_from"
date: 2009-08-08
forum: General Help
---

### Post by cbear on 2009-08-08
I am trying to feed a long list of addresses into spamassassin as blacklist_from values.  I can add them one by one into /home/tbegehr/mail/spamassassin/local.cf  ... no problem.  I am trying to feed the list into spamassassin using:

```
spamassassin --add-to-blacklist < address.list.file
```

I get this output from the command

```
SpamAssassin auto-whitelist: adding address to blacklist: customerservice@mymorepayhomeonline.info
SpamAssassin auto-whitelist: adding address to blacklist: JobAlerts@CyberCoders.com
SpamAssassin auto-whitelist: adding address to blacklist: listmaster@thegolfchannel.com
SpamAssassin auto-whitelist: adding address to blacklist: alerts@personals.yahoo.com
SpamAssassin auto-whitelist: adding address to blacklist: update@stubhub-mail.com
```

BUT, when I look at /home/tbegehr/mail/spamassassin/local.cf...they have not been added.  Where are they being added ?  Is it working ?

thanks much :)

---

