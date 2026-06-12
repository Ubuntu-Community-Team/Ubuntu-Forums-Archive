---
title: "Computer Sends Email to Me!?"
date: 2006-01-21
forum: General Help
---

### Post by ZedLord on 2006-01-21
Whenever I type 'finger subbu', I See there are new Mails,
All Mails read as
> 
From [email]root@subbu.co.in[/email]  Sat Jan 21 13:51:35 2006
X-Original-To: root
From: Anacron <root@subbu.co.in>
To: [email]root@subbu.co.in[/email]
Subject: Anacron job 'cron.daily' on Subbu
Date: Sat, 21 Jan 2006 13:51:35 +0530 (IST)

/etc/cron.daily/man-db:
mandb: warning: /usr/share/man/man1/rmic.1.gz is a dangling symlink
mandb: warning: /usr/share/man/man1/javaws.1.gz is a dangling symlink
mandb: warning: /usr/share/man/man1/rmiregistry.1.gz is a dangling symlink

Whats that!!!

---

### Post by dcstar on 2006-01-21
[QUOTE=ZedLord]Whenever I type 'finger subbu', I See there are new Mails,
All Mails read as


Whats that!!![/QUOTE]
Automated processes are run by the "cron" process, and the results are e-mailed to you Ubuntu user account.

Have a read of the messages, and in the case of "dangling symlinks", you can either delete them (or just ignore the messages.......)

---

