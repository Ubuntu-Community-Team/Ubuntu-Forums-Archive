---
title: "Confuring postfix to send to gmail"
date: 2009-10-07
forum: General Help
---

### Post by CharlesA on 2009-10-07
Hiya,

I found a [howto to use postfix thru gmail]("http://www.marksanborn.net/linux/send-mail-postfix-through-gmails-smtp-on-a-ubuntu-lts-server/"), but it's kind of confusing for me.

I don't get the whole CA deal.

I am running Ubuntu Server 9.04.

Background: I've got a RAID controller card in the server and the software can send an email to notify me if an error or warning occurs. Unfortunately when I try to send an email to any of the free webmail SMTP servers, the send fails. I'm guessing it's cuz the software doesn't support SSL or TSL.

Anyway, I was thinking of setting up postfix to relay those emails to gmail so I can get them, but I'm not sure how to go about doing that.

Any help is appreciated.

Thanks in advance.

EDIT: Just ended up using exim4 to send mail recieved on localhost:25. Works like a charm. :-)

---

