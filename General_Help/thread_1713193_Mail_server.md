---
title: "Mail server"
date: 2011-03-23
forum: General Help
---

### Post by vadimslav on 2011-03-23
Hi guys!
I bought VPS with Ubuntu installed and bound domain name to its IP. I want my site to have several emails like [email]support@<mysite>.com[/email], [email]sales@<mysite>.com[/email], [email]nypd@<mysite>.com[/email] etc. What should I install and is it possible to read emails sent on that address via my gmail account?

---

### Post by vadimslav on 2011-03-24
Anybody! Please!

---

### Post by SeijiSensei on 2011-03-24
> **vadimslav said:**
> Anybody! Please!

No one is likely to walk you through the process of setting up a mail server.  The best place to start is [https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix).

As for sending the messages to a gmail account, yes, you can do that by setting up "aliases" for each mailbox that point to a corresponding gmail address.

---

