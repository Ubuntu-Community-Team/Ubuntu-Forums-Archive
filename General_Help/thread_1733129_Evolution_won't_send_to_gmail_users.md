---
title: "Evolution won't send to gmail users"
date: 2011-04-18
forum: General Help
---

### Post by jripple on 2011-04-18
In general, sending to people with gmail accounts fails although it works for others.  Here's the error message:


Evolution Error
Error while Sending message.
RCPT TO <someuser@gmail.com>failed:
<someuser@gmail.com> No such user here

I have Evolution Sending Email set to Server Type: SMTP.


Help appreciated!!

Thanks.

---

### Post by jripple on 2011-04-18
Sorry, using Ubuntu 10.04.

Evolution v2.28.3

---

### Post by dcstar on 2011-04-20
> **jripple said:**
> In general, sending to people with gmail accounts fails although it works for others.  Here's the error message:


Evolution Error
Error while Sending message.
RCPT TO <someuser@gmail.com>failed:
<someuser@gmail.com> No such user here

I have Evolution Sending Email set to Server Type: SMTP.


**Exactly** what SMTP server?

And did you setup your system as "*your_name*@gmail.com"?

---

### Post by jripple on 2011-04-21
Thanks for your attention.

I'm not trying to connect to a gmail server with Evolution; only trying to send to people with gmail accounts like I'd send to anyone else.

I'm using the SMTP server of the outfit where I have my email account, which is not gmail.

Thanks,

---

### Post by Grenage on 2011-04-21
While this may sound illogical and unrelated, are you using authentication for outbound mail?  If not, can you try it?

---

### Post by jripple on 2011-04-25
Yes, I tried authentication for outbound mail but it didn't improve the situation.

---

### Post by alphacrucis2 on 2011-04-25
Maybe you could try another email program such as Thunderbird using the same smtp server that you use for evolution. If you still get the problem then you need to contact the administrator of the smtp server you are using. Maybe they don't like gmail.com accounts.

---

### Post by jripple on 2011-05-04
I retried enabling authentication for outbound mail.  I had to pay more attention to the SMTP password setup on the server which I had configured incorrectly.

This worked and my outbound mail folder emptied.

Thanks for the suggestion.

---

### Post by Grenage on 2011-05-04
> **jripple said:**
> I retried enabling authentication for outbound mail.  I had to pay more attention to the SMTP password setup on the server which I had configured incorrectly.

This worked and my outbound mail folder emptied.

Thanks for the suggestion.

Glad to hear it.

---

