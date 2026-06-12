---
title: "(mail,mailx) Setting the FROM field"
date: 2009-09-05
forum: General Help
---

### Post by sebrock on 2009-09-05
I'm really banging my head now ](*,)

I just can't get mail or mailx to set the from field using a configuration file like .mailrc

I need to do this because my SMTP provider has to acknowledge the address. So whenever I mail from my user account "sebastian" I want it to automatically change the FROM field like so:

Before: sebastian@localhost

After: [email]xxxxx@yahoo.com[/email]

This works using the -f flag with sendmail. However I need to use mail or mailx.

thanks

----

SOLVED: I edited postfix canonical sender maps instead.

---

