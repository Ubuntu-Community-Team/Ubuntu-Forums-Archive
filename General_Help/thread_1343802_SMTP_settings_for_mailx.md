---
title: "SMTP settings for mailx"
date: 2009-12-02
forum: General Help
---

### Post by yanvolking on 2009-12-02
Hello Community,

Can anyone tell me how to set the SMTP settings in mailx.  Ideally I would like to use mailx through my Gmail account.

Thanks

---

### Post by dcstar on 2009-12-03
> **yanvolking said:**
> Hello Community,

Can anyone tell me how to set the SMTP settings in mailx.  Ideally I would like to use mailx through my Gmail account.

Thanks

Mailx uses whatever MTA you have installed (like Postfix), that is where you configure things.

---

### Post by yanvolking on 2009-12-04
Hi Again,

Could the MTA in my case be EXIM4?  If not, how can I find out what it is?

thanks

Yan

---

### Post by kjohri on 2009-12-04
It could be exim4. You can see all the processes in the system by giving the command 

ps -ef

from the terminal. The MTA process could be sendmail/exim4/postfix, etc.

---

