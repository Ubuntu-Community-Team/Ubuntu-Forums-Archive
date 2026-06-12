---
title: "Command line email"
date: 2010-10-04
forum: General Help
---

### Post by markh86 on 2010-10-04
Hi,

I am looking to send emails from cron for backup information. However, all the programs I have found (mail, mutt) require the password in plain text. Does anyone know of a more secure method?

In fact, if it is only sending, is there a way to do this without logging into an account?

What is the simplest way, without making it check emails too?

Thanks for any help!

Mark

---

### Post by spiky001 on 2010-10-04
Have A look at Alpine I didn't have to put password in till it connects then it is just astrix, i,e like thunderbird dose

---

### Post by spjackson on 2010-10-04
> **markh86 said:**
> Hi,

I am looking to send emails from cron for backup information. However, all the programs I have found (mail, mutt) require the password in plain text. Does anyone know of a more secure method?

In fact, if it is only sending, is there a way to do this without logging into an account?

What is the simplest way, without making it check emails too?

Thanks for any help!

Mark
There are 2 main avenues:
1. Install and configure a fully fledged MTA such as postfix or exim, but these are probably over the top.
2. Send directly via SMTP to your ISP's SMTP host. There are several command line programs that do this, e.g. sendemail is a package in the repositories.

Whether you need to supply login credentials depends on your ISP.

---

### Post by markh86 on 2010-10-05
Thanks for the replies. I still do not understand though how this gives a secure and automated method?

I may just need to open a new email account with a password that doesn't matter if someone finds it.

Thanks.

Mark

---

