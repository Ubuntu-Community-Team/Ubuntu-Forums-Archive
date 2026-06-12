---
title: "Sendmail not liking email addresses from same domain as hostname"
date: 2010-03-19
forum: General Help
---

### Post by dgohn on 2010-03-19
Ok I have a problem and I believe that I have figured out why it is happening but I am not quite sure on how to fix it.

I am running several php scripts on my server that basically take user input from a webpage and e-mails it to specific addresses when submitted.  Basic e-mail form scripts.  The problem is that my servers hostname is set to mydomain.com and the e-mail addresses that the scripts are sending to are addresses such as [email]admin@mydomain.com[/email], [email]support@mydomain.com[/email].  Sendmail I believe is trying to route that message locally to the [email]admin@mydomain.com[/email] user or  support and so on instead of actually sending it out onto the net over the smtp server since my e-mail is actually hosted through my registrar. 

Does anyone know of a way to fix this or if this is actually what is happening?  And just as an added form of troubleshooting I threw in a yahoo email address instead in the script and it sent out just fine.  But as soon as I put [email]anything@mydomain.com[/email] in the script the script fails.

Thanks in advance for any and all help!

---

### Post by dgohn on 2010-03-19
*bump*

---

### Post by amauk on 2010-03-20
I don't have any experience with the original sendmail, but I do with postfix (which is sendmail compatible)
so this may or may not be of help

You should be able to edit which domains your mail transfer agent recognizes as "local"

In postfix, for example, there's a config entry called "mydestination"
by default, it'll be
```
mydestination = localhost, localhost@localdomain, mydomain.com
```

take out the mydomain.com entry and your mail server will send these externally

---

