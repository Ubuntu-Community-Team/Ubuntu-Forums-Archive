---
title: "trouble sending mail to google apps email"
date: 2010-08-31
forum: General Help
---

### Post by fahdoos on 2010-08-31
If i setup logwatch to send it's daily emails to my gmail account, it works fine.

```

Aug 31 19:57:31 XXXX postfix/smtp[1988]: 62B091223CD: to=<myemailaddress@gmail.com>, relay=gmail-smtp-in.l.google.com[74.125.65.27]:25, delay=1.6, delays=0.69/0.01/0.17/0.78, dsn=2.0.0, status=sent (250 2.0.0 OK 1283284645 d33si6705768and.106)

```

I have google apps setup for my domain, and sending emails from any regular email client to an email account on the domain is received properly by google apps email - for reference i'll call this email account [email]theman@XXXX.com[/email]. I have all the MX records for the domain pointing to google, etc, so all that seems correctly setup to me. 

The problem comes when I try to use this email address with logwatch for example, it seems like it's trying to resolve locally instead of sending externally to google...

```

Aug 31 19:56:57 XXXX postfix/pickup[1332]: D837B1223CD: uid=0 from=<root>
Aug 31 19:56:57 XXXX postfix/cleanup[1673]: D837B1223CD: message-id=<20100831195657.D837B1223CD@XXXX.com>
Aug 31 19:56:57 XXXX postfix/qmgr[29965]: D837B1223CD: from=<root@XXXX.com>, size=12318, nrcpt=1 (queue active)
Aug 31 19:56:57 XXXX postfix/local[1675]: D837B1223CD: to=<theman@XXXX.com>, relay=local, delay=0.79, delays=0.76/0.01/0/0.02, dsn=5.1.1, status=bounced (unknown user: "theman")
Aug 31 19:56:57 XXXX postfix/cleanup[1673]: E2550122504: message-id=<20100831195657.E2550122504@XXXX.com>
Aug 31 19:56:57 XXXX postfix/bounce[1676]: D837B1223CD: sender non-delivery notification: E2550122504
Aug 31 19:56:57 XXXX postfix/qmgr[29965]: E2550122504: from=<>, size=14004, nrcpt=1 (queue active)
Aug 31 19:56:57 XXXX postfix/qmgr[29965]: D837B1223CD: removed
Aug 31 19:56:57 XXXX postfix/local[1675]: E2550122504: to=<theman@XXXX.com>, orig_to=<root@XXXX.com>, relay=local, delay=0.02, delays=0.01/0/0/0.01, dsn=5.1.1, status=bounced (unknown user: "theman")
Aug 31 19:56:57 XXXX postfix/qmgr[29965]: E2550122504: removed

```

Any help would be appreciated!

---

### Post by Mr. C. on 2010-09-20
Create a local alias for root that forwards to the fully qualified google apps email address.  This will send all root mail.

If you only want logwatch's email, you'll have to change the logwatch invocation or config file to use a different email address.

---

### Post by fahdoos on 2010-11-24
So this seems to be a general issue with when any program on the server tries to send an email to the domain that the server is on. These should be going to the google servers due to the MX records... but I'm guessing I need to add something on the server to tell it to send the mails externally. Any ideas?

---

### Post by dcstar on 2010-11-25
> **fahdoos said:**
> So this seems to be a general issue with when any program on the server tries to send an email to the domain that the server is on. These should be going to the google servers due to the MX records... but I'm guessing I need to add something on the server to tell it to send the mails externally. Any ideas?

The server for that domain is not your server, you **cannot** have your server called the same as an external server serving that domain.

---

