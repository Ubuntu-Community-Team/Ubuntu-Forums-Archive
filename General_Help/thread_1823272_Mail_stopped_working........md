---
title: "Mail stopped working......."
date: 2011-08-11
forum: General Help
---

### Post by CVGH on 2011-08-11
I use fail2ban and it used to email me if it was stopped/started and if
there was a "attack".  This is the error I now see when checking my mail:
```
root@jupitermining:~# mail
"/var/mail/root": 3 messages 3 unread
>U   1 Mail Delivery Subs Thu Aug 11 18:47  69/2815  Postmaster notify: see transcript for details
 U   2 Mail Delivery Subs Thu Aug 11 18:49  68/2790  Postmaster notify: see transcript for details
 U   3 Mail Delivery Subs Thu Aug 11 19:00  68/2786  Postmaster notify: see transcript for details
? 3
Return-Path: <MAILER-DAEMON>
Received: from localhost (localhost)
    by localhost.localdomain (8.14.3/8.14.3/Debian-9.2ubuntu1) id p7BN025Z002742;
    Thu, 11 Aug 2011 19:00:02 -0400
Date: Thu, 11 Aug 2011 19:00:02 -0400
From: Mail Delivery Subsystem <MAILER-DAEMON>
Message-Id: <201108112300.p7BN025Z002742@localhost.localdomain>
To: postmaster
MIME-Version: 1.0
Content-Type: multipart/report; report-type=delivery-status;
    boundary="p7BN025Z002742.1313103602/localhost.localdomain"
Subject: Postmaster notify: see transcript for details
Auto-Submitted: auto-generated (postmaster-notification)
Status: O
X-UID: 3

This is a MIME-encapsulated message

--p7BN025Z002742.1313103602/localhost.localdomain

The original message was received at Thu, 11 Aug 2011 19:00:01 -0400
from localhost.localdomain [127.0.0.1]

   ----- The following addresses had permanent fatal errors -----
<xraym18@gmail.com>
    (reason: 550-5.7.1 [xx.xx.xx.xx] The IP you're using to send mail is not authorized to)

   ----- Transcript of session follows -----
... while talking to gmail-smtp-in.l.google.com.:
>>> DATA
<<< 550-5.7.1 [xx.xx.xx.xx] The IP you're using to send mail is not authorized to
<<< 550-5.7.1 send email directly to our servers. Please use the SMTP relay at your
<<< 550-5.7.1 service provider instead. Learn more at                         
<<< 550 5.7.1 http://mail.google.com/support/bin/answer.py?answer=10336 ef1si5424387qab.65
554 5.0.0 Service unavailable
550 5.1.1 <fail2ban@localhost6.localdomain6>... User unknown

--p7BN025Z002742.1313103602/localhost.localdomain
Content-Type: message/delivery-status

Reporting-MTA: dns; localhost.localdomain
Received-From-MTA: DNS; localhost.localdomain
Arrival-Date: Thu, 11 Aug 2011 19:00:01 -0400

Final-Recipient: RFC822; xraym18@gmail.com
Action: failed
Status: 5.7.1
Remote-MTA: DNS; gmail-smtp-in.l.google.com
Diagnostic-Code: SMTP; 550-5.7.1 [xx.xx.xxx.xx] The IP you're using to send mail is not authorized to
Last-Attempt-Date: Thu, 11 Aug 2011 19:00:02 -0400

--p7BN025Z002742.1313103602/localhost.localdomain
Content-Type: text/rfc822-headers

Return-Path: <fail2ban@localhost6.localdomain6>
Received: from localhost6.localdomain6 (localhost.localdomain [127.0.0.1])
    by localhost.localdomain (8.14.3/8.14.3/Debian-9.2ubuntu1) with ESMTP id p7BN015Z002740
    for <xraym18@gmail.com>; Thu, 11 Aug 2011 19:00:01 -0400
Received: (from root@localhost)
    by localhost.localdomain (8.14.3/8.14.3/Submit) id p7BMqrBC001712
    for xraym18@gmail.com; Thu, 11 Aug 2011 18:52:53 -0400
Date: Thu, 11 Aug 2011 18:52:53 -0400
Message-Id: <201108112252.p7BMqrBC001712@localhost.localdomain>
Subject: [Fail2Ban] ssh: started
From: Fail2Ban <fail2ban@localhost6.localdomain6>
To: xraym18@gmail.com

--p7BN025Z002742.1313103602/localhost.localdomain--

```Why would the email have stopped working?

---

