---
title: "How to Change Email Message-ID"
date: 2010-03-23
forum: General Help
---

### Post by supradave on 2010-03-23
I have my main email server for my company and then I have some satellite systems, e.g. CRM that can send out emails to customers.  For emails that come out of my satellite systems, I would just like company.com rather than crm.company.com in the header, particularly in the Message-ID.

The satellite server is 8.10 server with the default mailer exim4, which I'm not as familiar with as Postfix.

Here's an example header:
```
Return-Path: <sales@company.com>
Received: from mail.company.com ([unix socket])
        by s64s-mail (Cyrus ) with LMTP; Tue, 23 Mar 2010 10:41:31 -0600
X-Sieve: CMU Sieve 2.2
Received: by mail.company.com (Postfix, from userid 65534)
        id 9111210A6FD2B; Tue, 23 Mar 2010 10:41:31 -0600 (MDT)
Received: from crm (crm.company.com [10.0.0.1])
        by mail.company.com (Postfix) with ESMTP id ACD3E10A6FCF5
        for <dave@company.com>; Tue, 23 Mar 2010 10:41:30 -0600 (MDT)
Date: Tue, 23 Mar 2010 10:40:30 -0600
To: Dave <dave@company.com>
From: Sales Development <sales@company.com>
Subject: Thank you for your interest...
Message-ID: <013adc840814e66d6a60e1ede3e871dc@crm>
```

Thanks for any help.

---

