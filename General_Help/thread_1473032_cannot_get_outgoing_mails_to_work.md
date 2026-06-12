---
title: "cannot get outgoing mails to work"
date: 2010-05-04
forum: General Help
---

### Post by orweinberger on 2010-05-04
Hey, I installed postfix + SASL on my ubuntu box, getting emails works 100%.

Sending out emails does not work. i'm getting "554 5.7.1 - Relay access denied".

Any ideas what the problem could be? 

(main.cf = [http://pastebin.com/uEzkMWjN](http://pastebin.com/uEzkMWjN)).

Thanks!

---

### Post by rturner on 2010-05-04
Try uncommenting:

relayhost =

Leave it like that to let localhost relay your mail.  And normally myhostname lists the machine name too:

myhostname = machinename.domainname.com

---

### Post by orweinberger on 2010-05-04
Did that, does not work.

When I try sending out email I get the message I wrote in my original post.

To my understanding, sasl is installed to prevent me from having to constantly change the mynetworks to contain the sender IP address (which in my case is dynamic so i cannot keep redefining it).

When I set the mynetworks to be defined for my current IP address, sending out emails through smtp _without authentication_ works.

When I remove the mynetworks to be as in my pastebin post and try sending out an email _without authentication_, i'm getting the "Relay access denied".

When I do try authenticating to the smtp server, it does not let me go through (password/username wrong). even though i use mysql for all the users, and it uses the same db as for the imap service which works 100%.

Anyone knows what could be the issue here?

Thanks!

---

### Post by dcstar on 2010-05-05
> **orweinberger said:**
> 
.........
When I set the mynetworks to be defined for my current IP address, sending out emails through smtp _without authentication_ works.

When I remove the mynetworks to be as in my pastebin post and try sending out an email _without authentication_, i'm getting the "Relay access denied".



**mynetworks** is for the INTERNAL IP address range of anything that wants to use your SMTP server to send emails, it has nothing to do with your external IP address unless your network hosts public IPs.

---

### Post by lisati on 2010-05-05
Try using authenticating with your user name & TLS or SSL in your email client

---

