---
title: "Configure email for sending automatic emails?"
date: 2011-09-20
forum: General Help
---

### Post by windyweather on 2011-09-20
I'm getting tired of keeping my 3 linux systems up to date and want to set up automatic updates.
I followed these instructions:
[https://help.ubuntu.com/community/AutomaticSecurityUpdates](https://help.ubuntu.com/community/AutomaticSecurityUpdates)

I'd like to get an email when something goes wrong.
after a bunch of digging around, I found this:
[http://klenwell.com/press/2009/03/ubuntu-email-with-mailx/](http://klenwell.com/press/2009/03/ubuntu-email-with-mailx/)

but I don't want to use GMAIL, I want to use GMX.com and this looks like it is setting things up so that I can send email from my user account. I'm not clear that the cron jobs run in that context.

Can someone point me to the instructions for setting up mailx [or something that will work with cron jobs] so that I can get emails when my auto updates go off. Currently I've set things to send an email whether they succeed or fail, but eventually I want failure only and I'll flip that switch in the config.

```
BTW, I get the following in the mail log file:
2011-09-20 10:29:40 1R648a-0005XZ-90 <= wwdummy@squall-ubuntu U=wwdummy P=local S=407
2011-09-20 10:29:40 1R648a-0005XZ-90 ** wwdummy@gmx.com R=nonlocal: Mailing to remote domains not supported
2011-09-20 10:29:40 1R648a-0005Xb-BP <= <> R=1R648a-0005XZ-90 U=Debian-exim P=local S=1239
2011-09-20 10:29:40 1R648a-0005XZ-90 Completed
2011-09-20 10:29:40 1R648a-0005Xb-BP => wwdummy <wwdummy@squall-ubuntu> R=local_user T=mail_spool
2011-09-20 10:29:40 1R648a-0005Xb-BP Completed
```

Thanks,
ww

---

### Post by dcstar on 2011-09-21
> **windyweather said:**
> 
........
but I don't want to use GMAIL, I want to use GMX.com and this looks like it is setting things up so that I can send email from my user account.
........

Simply install the **postfix** package and let the Ubuntu system send the e-mails.

---

### Post by windyweather on 2011-09-21
> **dcstar said:**
> Simply install the **postfix** package and let the Ubuntu system send the e-mails.

Looking at this page:
[https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto)

Seems that Postfix is a mail receiver, not a mail sender. Right? I don't want to receive email on this system. I want to send mail from this system.

Thanks,
- ww

---

### Post by dcstar on 2011-09-22
> **windyweather said:**
> Looking at this page:
[https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto)

Seems that Postfix is a mail receiver, not a mail sender. Right? I don't want to receive email on this system. I want to send mail from this system.


Postfix is an MTA, it sends e-mails **you** submit to it to internal or external destinations.

It turns your system into a mail server so you **don't** have to use external mail servers - which is what you specifically asked for initially.

---

### Post by windyweather on 2011-09-22
Thanks, David. But how do I configure something to do my job?
Anybody? Link to a page that shows me how to configure something to send mail to an external email address?
Thanks,
ww

---

### Post by Cheesehead on 2011-09-24
Here's one way to do it using the 'nail' command, including crontab examples.

See [http://cheesehead-techblog.blogspot.com/search/label/nail](http://cheesehead-techblog.blogspot.com/search/label/nail)

nail, back when those were written, was a standalone package. That changed, and nail is now included in the 'heirloom-mailx' package.

---

