---
title: "sendmail not working?"
date: 2012-03-28
forum: General Help
---

### Post by qwertyjjj on 2012-03-28
I am trying to test sendmail as it seems to have stopped sending emails.
Any ideas what could be wrong?

Mar 28 13:51:06 jason sendmail[2226]: STARTTLS=client, relay=mx2.servage.net., version=TLSv1/SSLv3, verify=FAIL, cipher=DHE-RSA-AES256-SHA, bits=256/256
Mar 28 13:51:06 jason sendmail[2226]: q2SBp4MY002224: to=<xxx@pxxx.fr>, ctladdr=<root@jason.xxxxx.com> (0/0), delay=00:00:02, xdelay=00:00:02, mailer=esmtp, pri=120296, relay=mx2.servage.net. [77.232.76.20], dsn=4.1.8, stat=Deferred: 450 4.1.8 <root@localhost.localdomain>: Sender address rejected: Domain not found

---

### Post by jim_deadlock on 2012-03-28
It looks like the mail server you're sending the email to is rejecting the mail because it doesn't recognise your own domain. Have you tried sending mail to a different address just to check it?

---

### Post by qwertyjjj on 2012-03-28
seems to be working sometimes and not others?

Mar 28 17:30:07 myname sendmail[3351]: q2SFU6LT003351: to=aide@mysite.fr, ctladdr=root (0/0), delay=00:00:01, xdelay=00:00:00, mailer=relay, pri=30430, relay=[127.0.0.1] [127.0.0.1], dsn=2.0.0, stat=Sent (q2SFU78R003356 Message accepted for delivery)
Mar 28 17:30:08 myname sendmail[3358]: STARTTLS=client, relay=mx1.servage.net., version=TLSv1/SSLv3, verify=FAIL, cipher=DHE-RSA-AES256-SHA, bits=256/256
Mar 28 17:30:08 myname sendmail[3355]: q2SFU6KH003353: to=<blahenero4@hotmail.com>, ctladdr=<root@myname.dns26.com> (0/0), delay=00:00:02, xdelay=00:00:02, mailer=esmtp, pri=121397, relay=mx4.hotmail.com. [65.55.92.184], dsn=2.0.0, stat=Sent ( <201203281530.q2SFU6XP003352@myname.dns26.com> Queued mail for delivery)
Mar 28 17:30:08 myname sendmail[3358]: q2SFU78R003356: to=<aide@mysite.fr>, ctladdr=<root@myname.dns26.com> (0/0), delay=00:00:01, xdelay=00:00:01, mailer=esmtp, pri=120669, relay=mx1.servage.net. [77.232.76.20], dsn=4.1.8, stat=Deferred: 450 4.1.8 <root@localhost.localdomain>: Sender address rejected: Domain not found
Mar 28 17:30:08 myname sendmail[3358]: STARTTLS=client, relay=mx2.servage.net., version=TLSv1/SSLv3, verify=FAIL, cipher=DHE-RSA-AES256-SHA, bits=256/256
Mar 28 17:30:09 myname sendmail[3358]: q2SFU78R003356: to=<aide@mysite.fr>, ctladdr=<root@myname.dns26.com> (0/0), delay=00:00:02, xdelay=00:00:02, mailer=esmtp, pri=120669, relay=mx2.servage.net. [77.232.76.20], dsn=4.1.8, stat=Deferred: 450 4.1.8 <root@localhost.localdomain>: Sender address rejected: Domain not found
Mar 28 17:37:57 myname sendmail[3400]: alias database /etc/aliases rebuilt by root
Mar 28 17:37:57 myname sendmail[3400]: /etc/aliases: 77 aliases, longest 19 bytes, 788 bytes total

---

### Post by jim_deadlock on 2012-03-28
The difference is probably that some of the mail servers use sender address verification and others don't. Your address doesn't pass the verification process because the domain doesn't have a proper MX record.

It's nothing to do with sendmail, that's working fine, it's just your dodgy sender email address. Try putting a valid Gmail or Yahoo addy in the From: field and see what happens.

---

### Post by smtp on 2012-04-23
The problem is that "localhost.localdomain" does not exists in the Internet. Most of the e-mail servers will refuse to accept messages form non-existing domains.

---

### Post by qwertyjjj on 2012-04-26
> **smtp said:**
> The problem is that "localhost.localdomain" does not exists in the Internet. Most of the e-mail servers will refuse to accept messages form non-existing domains.

yes, but where in the server is localhost.localdomain listed.
What conf file is it in?

---

