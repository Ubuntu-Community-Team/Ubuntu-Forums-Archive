---
title: "Help with a mail solution."
date: 2012-03-28
forum: General Help
---

### Post by Mercedes300 on 2012-03-28
Hi all.

I want to access my mail via IMAP, but I get a ton of email. So much, that right now I have 46GB! This would fill up my mail server in short order. I would only like to have a months worth of email on the server (being served by IMAP) at a time.

I think a solution where I could pull off the email older than a month to archive locally, removing it from the server, would be good.

could this be done with fetchmail or something like it.  

Please help me oh mail gurus! :)

-John

---

### Post by SeijiSensei on 2012-03-28
Do you have control over the server?  An easy way to rotate mail is to create a configuration file in the server's /etc/logrotate.d/ for /var/spool/mail/username.

---

### Post by dcstar on 2012-03-30
> **Mercedes300 said:**
> Hi all.

I want to access my mail via IMAP, but I get a ton of email. So much, that right now I have 46GB! This would fill up my mail server in short order.
.........

If you are "accessing" e-mail via IMAP then you do **not** have a mail **server**, you have a mail **client**.

Simply leave the mail where it is now and use a decent IMAP mail client to access them, only the messages you need to read are ever downloaded.

---

