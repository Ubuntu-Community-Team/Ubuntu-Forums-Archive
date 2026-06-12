---
title: "Cant send mail? (local SMTP server)"
date: 2012-01-12
forum: General Help
---

### Post by samvkampen on 2012-01-12
Ohai.

So, I can't send mail via my MTA, (postfix), I get the following error.

> 421 4.3.0 collect: Cannot write ./dfq0CGhQA4007785 (bfcommit, uid=0, gid=107): No such file or directoryI tried reinstalling everything, did not help. I could send mail before...

I also tried configuring SquirrelMail and that says Connection to IMAP server lost when I login (but thats another story)...

[EDIT: Connection issue fixed, get other errors now... Stuff like
> **[COLOR=#cc0000]ERROR: Could not complete request.[/COLOR]**[COLOR=#cc0000]
Query: SELECT "INBOX"
Reason Given: [SERVERBUG] Internal error occurred. Refer to server log for more information. [2012-01-12 19:55:23][/COLOR]]

[EDIT: Okay, the first error made no sense (that I had here).. mail.log here:
[http://aperture.mangeh.net/mail.log](http://aperture.mangeh.net/mail.log)
I run Postfix and Dovecot.

Any replies appreciated,

Sam

---

### Post by Frantique on 2012-03-05
You must chmod to 0600 the mail spool file for the user, after that will work.

---

