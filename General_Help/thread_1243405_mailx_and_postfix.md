---
title: "mailx and postfix"
date: 2009-08-18
forum: General Help
---

### Post by buffy^ on 2009-08-18
I have just tried to install mailx and post fix and when attempting to send a message I get the error below:


I type this:
```

mailx bob@amg-it.co.uk
subject:test1
test1
EOT 

```

and get this:
```

Message 1:
From MAILER-DAEMON  Tue Aug 18 15:17:55 2009
X-Original-To: bob@serenity-oversight
Date: Tue, 18 Aug 2009 15:17:55 +0100 (BST)
From: MAILER-DAEMON@serenity-oversight (Mail Delivery System)
Subject: Undelivered Mail Returned to Sender
To: bob@serenity-oversight
Auto-Submitted: auto-replied
MIME-Version: 1.0
Content-Type: multipart/report; report-type=delivery-status;
        boundary="4B1E7304C0.1250605075/serenity-oversight"

This is a MIME-encapsulated message.

--4B1E7304C0.1250605075/serenity-oversight
Content-Description: Notification
Content-Type: text/plain; charset=us-ascii

This is the mail system at host serenity-oversight.

I'm sorry to have to inform you that your message could not
be delivered to one or more recipients. It's attached below.

For further assistance, please send mail to postmaster.

If you do so, please include this problem report. You can
delete your own text from the attached returned message.

                   The mail system

<bob@amg-it.co.uk>: localdomain

--4B1E7304C0.1250605075/serenity-oversight
Content-Description: Delivery report
Content-Type: message/delivery-status

Reporting-MTA: dns; serenity-oversight
X-Postfix-Queue-ID: 4B1E7304C0
X-Postfix-Sender: rfc822; bob@serenity-oversight
Arrival-Date: Tue, 18 Aug 2009 15:17:55 +0100 (BST)

Final-Recipient: rfc822; bob@amg-it.co.uk
Action: failed
Status: 5.0.0
Diagnostic-Code: X-Postfix; localdomain

--4B1E7304C0.1250605075/serenity-oversight
Content-Description: Undelivered Message
Content-Type: message/rfc822

Received: by serenity-oversight (Postfix, from userid 1000)
        id 4B1E7304C0; Tue, 18 Aug 2009 15:17:55 +0100 (BST)
To: bob@amg-it.co.uk
Subject: test1
Message-Id: <20090818141755.4B1E7304C0@serenity-oversight>
Date: Tue, 18 Aug 2009 15:17:55 +0100 (BST)
From: bob@serenity-oversight (bob)

```

---

### Post by dcstar on 2009-08-19
> **buffy^ said:**
> I have just tried to install mailx and post fix and when attempting to send a message I get the error below:
........

```
dpkg-reconfigure postfix
```

Select "Internet".

---

### Post by buffy^ on 2009-08-19
That worked a charm thanks very much.

---

