---
title: "Emails getting classified as spam"
date: 2009-11-03
forum: General Help
---

### Post by honestguvnor on 2009-11-03
I am trying to set up a mail server at home. Mail is sent and received without problem but the receiver often, though not always, classifies the mail as spam. Can someone please point me at some information about how to sort why this happening and what I can do to fix it. Many thanks.

---

### Post by P4man on 2009-11-03
Are you on a dynamic DNS host? 

> Next you need to decide whether to send all outgoing mail via another SMTP server, or send them yourself. I send via my ISP's server, so it has to worry about the queing etc. If you send it yourself then you are not reliant on 3rd party server. **But you may risk more exposure and accidentally be blocked by spam blockers**. And it is more work for your server. Also **many servers block dynamic dns hosts,** so you may find your server gets rejected. However choose whichever you are comfortable with. 

[http://flurdy.com/docs/postfix/#app_why](http://flurdy.com/docs/postfix/#app_why)

---

### Post by mike555 on 2009-11-03
if your email address is in their address book it should not be set as spam ....

---

### Post by honestguvnor on 2009-11-03
> Are you on a dynamic DNS host? 

Thanks for the link. Yes I have a dynamic IP and it looks like it could be the problem. I can try to talk to my IP provider about using their SMTP server but they have not proved helpful in the past. 

> if your email address is in their address book it should not be set as spam ....

Indeed but if my email goes in their spam bin they will never see it in the first place. Today was the first time I looked in the spam bin of any of my free web accounts for months.

---

