---
title: "Logcheck can't send email."
date: 2011-01-04
forum: General Help
---

### Post by mail2345 on 2011-01-04
I have two computers running ubuntu, a server, and my desktop.
Server has postfix for receiving mail, and dovecot for reading it.
Server has logcheck installed, and it can send alerts to my email account on the server.
However, logcheck on my desktop can't send emails. I can telnet from my local computer and manually send emails.
EDIT:
Solved by having evolution check local mail spool, and having desktop logcheck send to localhost.

---

