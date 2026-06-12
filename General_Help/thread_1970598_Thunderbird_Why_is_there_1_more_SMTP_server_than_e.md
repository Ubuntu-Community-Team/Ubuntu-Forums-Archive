---
title: "Thunderbird: Why is there 1 more SMTP server than email accounts?"
date: 2012-05-01
forum: General Help
---

### Post by rocksockdoc on 2012-05-01
In Thunderbird, I have three IMAP email accounts loaded and these work just fine (except sending mail is slow and it barfs often when saving mail). 

In debugging, I doublechecked that I have one SMTP server set for each account (one is gmail, one is for the company, and another is for a godaddy account - all of which use different SMTP servers).

However, one thing confuses me.

Thunderbird seems to enforce a FOURTH server (one more than the number of accounts) in the LOCAL FOLDERs section at the bottom of the left-most panel.

Local Folders
- Junk Settings
- Disk Space
- Outgoing Server (SMTP)   <=== what is this?

Since I already set a different SMTP server for my three email accounts, what do I do with this fourth SMTP server? What does it even exist?
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=217036&stc=1&d=1335890987[/IMG]

---

### Post by SeijiSensei on 2012-05-01
Did you not try clicking the "Outgoing Server" item?  It offers you a list of all the SMTP servers you have configured and allows you to set one as the default, modify their settings like IP addresses, etc.  It's not another server; it's the option to configure the servers you have defined or to add additional servers.

---

### Post by rocksockdoc on 2012-05-01
> **SeijiSensei said:**
>  It's not another server; it's the option to configure the servers you have defined or to add additional servers.

Thanks for the advice.

I see that it is a list of the existing three SMTP servers (one for each account), with the option to change settings.

But, since each account uses its own SMTP server, and since I 'want' each account to use its own SMTP server ... why must I set a "default" SMTP server in this location?

For example, I have three accounts, each with their own SMTP server:
 Account1 SMTP server = smtp.gmail.com
 Account2 SMTP server = smtp.godaddy.com
 Account3 SMTP server = smtp.secureserver.net

The problem I have understanding this server setting is that it FORCES me to set one of those as a default. 

But I don't want any of those to be used for any other account than the one which it's assigned to.

What don't I understand?

Why is Thunderbird forcing me to set a default SMTP server when I've clearly set a separate server for each account? (Please advise as I'm not sure WHAT is happening - but I do know I have VERY SLOW mail actions).

---

### Post by SeijiSensei on 2012-05-01
Even if you set a default, you can override it in the individual account settings.  Just pick one, presumably the one you use most often, then set the others as needed.

Not everyone uses the matching server for each account.  I have a server in my office that I can use to send mail with a From address in various accounts.  There was once a time before mail consisted of 99% spam when this was generally an acceptable practice.  Nowadays with things like "Sender Preferred From" it's getting harder and harder to use just one SMTP server for outbound mail.

---

### Post by rocksockdoc on 2012-05-01
> **SeijiSensei said:**
> Even if you set a default, you can override it in the individual account settings.  Just pick one, presumably the one you use most often, then set the others as needed.

Ah. I see. I think. 

So what you're saying is that the individual settings will be used (which is what they're there for); but if there is a 'problem', then, perhaps, the default SMTP server will be used?

Thanks for the advice.

Since it's the most generic, I guess I'll set the gmail SMTP server as the default ... just in case.

---

