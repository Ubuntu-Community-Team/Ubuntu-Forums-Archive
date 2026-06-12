---
title: "Please help with evolution"
date: 2010-09-19
forum: General Help
---

### Post by TroN-0074 on 2010-09-19
for like two weeks I have been trying to send email using evolution for some reason I always get the same ```
Could not connect to smtp.gmail.com: Input/output error
```
Can somebody please advice on what to do there. I will appreciate it.

---

### Post by gandaran on 2010-09-20
> **TroN-0074 said:**
> for like two weeks I have been trying to send email using evolution for some reason I always get the same ```
Could not connect to smtp.gmail.com: Input/output error
```
Can somebody please advice on what to do there. I will appreciate it.
can you post a screenshot of the evolution smtp gmail window setup?
this would be the best way to figure out the problem quickly (erase your gmail only) or post exactly the setup details.

---

### Post by TroN-0074 on 2010-09-20
Thank you this is how I have it set up. My Hotmail account has the same problem too

---

### Post by Quackers on 2010-09-20
Just an idea, as I don't use gmail, is it possible that it needs SSL encryption? I have only seen SSL used with gmail before.

---

### Post by TroN-0074 on 2010-09-20
ssl encriptation in the incoming mail, tls in the outgoing mail

---

### Post by plucky on 2010-09-20
My gmail account requires me to use a different ports for imap accounts

Setting for gmail:-> Incoming Mail (IMAP) Server - requires SSL: 	imap.gmail.com
Use SSL: Yes
Port: 993
Outgoing Mail (SMTP) Server - requires TLS: 	smtp.gmail.com (use authentication)
Use Authentication: Yes
Use STARTTLS: Yes (some clients call this SSL)
Port: 465 or 587
Account Name: 	your full email address (including @gmail.com) Google Apps users, please enter [email]username@your_domain.com[/email]
Email Address: 	your full Gmail email address (username@gmail.com) Google Apps users, please enter [email]username@your_domain.com[/email]
Password: 	your Gmail password 

**smtp.gmail.com:465**
**imap.gmail.com:993**

---

### Post by gandaran on 2010-09-21
> **TroN-0074 said:**
> Thank you this is how I have it set up. My Hotmail account has the same problem too
well I don't see anything wrong, I use SSL encryption and on the username field just the username not the full email and it work very well! try the SSL and enable the remember password too.
the problem could be blocked outgoing ports, did you install any firewall gui?

---

