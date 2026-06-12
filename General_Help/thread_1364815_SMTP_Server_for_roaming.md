---
title: "SMTP Server for roaming"
date: 2009-12-26
forum: General Help
---

### Post by pokerbirch on 2009-12-26
I'm sure this must be a common problem, yet Google hasn't really helped me. On my desktop PC, i normally setup my SMTP mail server to use the one provided by my ISP.

I also have a Netbook running Ubuntu Remix and have recently discovered that when connected to the internet via different ISP's, i can no longer send emails. I have several email accounts, 2 of which are gmail, so i attempted to use the gmail SMTP settings for ALL mail accounts. On my none-gmail accounts, i get a "relaying denied" error (which was not unexpected). I want to avoid "free" public smtp servers because they are generally spam hell.

So what are my options? Could (or should) i setup a private SMTP server on one of my own websites? Can i setup an SMTP server/proxy on my netbook via localhost? I am comfortable with Python and PHP programming...if a bespoke solution is required.

TYIA.

---

### Post by pokerbirch on 2009-12-26
After playing around with Postfix, i decided to look for an easier solution. This led me to solving the problem by routing all outgoing mail through Gmail. Initially, the "From:" header was incorrect but that can be fixed by specifying a custom header:

[http://mail.google.com/support/bin/answer.py?hl=en&answer=22370](http://mail.google.com/support/bin/answer.py?hl=en&answer=22370)

I am no longer getting the "relaying" problem but that may be due to the server naming - i was previously using smtp.googlemail.com and am now using smtp.gmail.com.

---

### Post by dcstar on 2009-12-27
> **pokerbirch said:**
> After playing around with Postfix, i decided to look for an easier solution. This led me to solving the problem by routing all outgoing mail through Gmail. Initially, the "From:" header was incorrect but that can be fixed by specifying a custom header:

[http://mail.google.com/support/bin/answer.py?hl=en&answer=22370](http://mail.google.com/support/bin/answer.py?hl=en&answer=22370)

I am no longer getting the "relaying" problem but that may be due to the server naming - i was previously using smtp.googlemail.com and am now using smtp.gmail.com.

An Ubuntu install **is** a SMTP server. You simply use the default postfix installation and set your mail client to use it (in Evolution it is the "Sendmail" option).

---

