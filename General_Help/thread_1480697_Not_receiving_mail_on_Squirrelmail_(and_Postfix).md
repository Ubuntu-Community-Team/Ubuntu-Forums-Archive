---
title: "Not receiving mail on Squirrelmail (and Postfix?)"
date: 2010-05-11
forum: General Help
---

### Post by SuaSwe on 2010-05-11
Evening everyone,

I've just configured my server with Postfix and Squirrelmail and am testing sending and receiving mail. Sending mail (via Squirrelmail) is working fine, as well as receiving mail from that same account, but it will not accept mail from external e-mail accounts, such as Gmail and Hotmail; I can however send mail to those addresses from Squirrelmail with no problems. 

The bounceback message I get from Google is as follows:

> Google tried to deliver your message, but it was rejected by the recipient domain. We recommend contacting the other email provider for further information about the cause of this error. The error that the other server returned was: 550 550 #5.1.0 Address rejected "mail@mydomain.com" (state 14).

Could it be that I need to register a mailbox with the people hosting my domain (please no!) or is there something I can do in Postfix or elsewhere on my server that will let the great interwebs recognise my e-mail address?

Note that I tested the mailbox using the tool at [http://mailboxtools.com/tools/smtptest.aspx](http://mailboxtools.com/tools/smtptest.aspx) and all came back clear and apparently working fine.

Any ideas? Thanks muchly!

---

### Post by SuaSwe on 2010-05-12
Bump?

---

### Post by SuaSwe on 2010-05-12
Does anyone know if there's a better forum section to post this in? I've scoured the internets for a solution but nothing doing! 

The apps I'm using are:
- Postfix (MTA)
- Courier (IMAP/POP3)
- Squirrelmail (Webmail client, for viewing/testing)

As mentioned, I worry that I need to have an e-mail address registered with my domain provider in order to receive mail to my server (which services my domain), but I'm not sure if this is the case, or if I could use my existing server username - I am able to log into that mail account via Squirrelmail and send mail from it no problem, and it seems to test fine from random testers attempted on the net. Would appreciate any tips or guidance as I am somewhat out of my depth here. :D

Thanks all,

Suave

---

### Post by SuaSwe on 2010-05-12
Marking this as solved - a genius friend helped me! 

For anyone experiencing the same problem, this is what was going on:

From Terminal, running:

```

dig -t mx suaserve.com

```

... showed my MX record as belonging to my domain provider, meaning that my mail was being routed incorrectly. All I had to do was to direct my MX record to point to my server instead - doing this was a simple matter of navigating to my account on GoDaddy's (e.g. my domain provider's) website and updating my MX record to mydomain.com, instead of their default, mailstore1.secureserver.net. Gave it a couple of hours and all is now working nicely!

Thanks for listening,

Suave

---

