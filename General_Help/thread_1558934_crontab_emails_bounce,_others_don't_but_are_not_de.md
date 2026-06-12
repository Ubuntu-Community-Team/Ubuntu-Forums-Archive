---
title: "crontab emails bounce, others don't but are not delivered"
date: 2010-08-22
forum: General Help
---

### Post by samwilsonau on 2010-08-22
Does anyone know what might be causing the following situation?

Crontab emails are bouncing with the message "Message rejected as spam by Content Filtering." (I've contacted the mail server admin about this.)

But emails sent with the command "mail [EMAIL="user@example.com"]user@example.com[/EMAIL]" etc. are "stat=Sent ... Queued mail for delivery" (according to the log), but never arrive and never bounce. I've tried sending as root and as other users.

Any help would be greatly appreciated!  Thanks.

---

### Post by samwilsonau on 2010-08-23
There was no PTR DNS record for the hostname I was sending from, and so the remote host refused to deliver them.  I don't know what caused the disparity in responses for emails sent from cron vs. emails sent from elsewhere, but the issue is now fixed.  The sysadmin of the mail server whitelisted the sending hostname.

---

### Post by amauk on 2010-08-23
This sort of thing is getting quite common
It's all in the name of spam prevention

Also, quite a few ISP's reject mail from mailservers operating on residential IP blocks

I run my own mailserver too
but route all incoming & outgoing mail through gmail
(too many issues otherwise)

---

### Post by samwilsonau on 2010-08-23
Yeah, I can imagine that there would be no end of work in running a internet-exposed mail server; not something I want to take on!  The server in question here is within a corporate network, and is only sending to other internal machines; I suspect the DNS isn't set up as rigorously as it could be.  But I'm just a lowly coder, and sysadmining isn't my forte.

---

