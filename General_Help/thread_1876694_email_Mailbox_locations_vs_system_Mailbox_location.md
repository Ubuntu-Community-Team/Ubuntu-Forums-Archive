---
title: "email Mailbox locations vs system Mailbox locations"
date: 2011-11-06
forum: General Help
---

### Post by bergqvistjl on 2011-11-06
Hi, I'm trying to set up mail on my system (it's a bit archaic, its more of an excercise tbh) and I'm running into a problem. I've currently successfully set up an SMTP server (running on postfix), which is configured so that every user on my system has their own mail adress which can be emailed from outside (i.e. [email]user@domain.com[/email]) and also of course if you want to contact another local user, you can just go user@hostname which just sends the message internally so to speak, anyway - this is how they are currently set up: 

external (via SMTP) messages: go to [Home_Dir of that user]/Mail in the MailDir format

local messages: go to /var/mail/Username in mbox format and ALSO shows up as "you have new mail" when you log in.

Now, while it's fine for (what I call) the external (SMTP) emails, I would prefer to have any local messages in the MailDir format, like the external ones, and in the same location, yet also have the "you have new mail" message whenever I have new mail when I log in, whether I have new local and/or external mail, not just for local messages?

So yeah, is it possible to switch from using the mbox format to MailDir, for local messages, without mailx (I need to keep it compatiable for mailx/mail, its currently annoying as I have to modify the $MAIL environment variable every time I want to check my MailDir messages, as it defaults to the mbox configuration every time) shouting at me?

Thanks, so to summarise, I want to have my mailer use MailDir, rather than mbox for local messages, to bring it in line with how messages coming in from outside my server are dealt with. is this possible, and if so - how?

---

### Post by bluexrider on 2011-11-06
Change your E-mail Client default folders location.

---

### Post by bergqvistjl on 2011-11-06
> **bluexrider said:**
> Change your E-mail Client default folders location.

My email client is mailx (the commandline one). Where would the config file be for that?

---

### Post by bluexrider on 2011-11-06
[http://linux.die.net/man/1/mailx](http://linux.die.net/man/1/mailx)

This may help

---

### Post by bergqvistjl on 2011-11-06
> **bluexrider said:**
> [http://linux.die.net/man/1/mailx](http://linux.die.net/man/1/mailx)

This may help

I'm not sure where to look :$ I just want to switch from storing local messages in mbox format, to maildir, permanently.

---

### Post by bergqvistjl on 2011-11-06
I think it must be on the server side I need to change, to store local mail in a Maildir with the external mail, rather than in mbox format on its own. But I don't know how :S

---

### Post by bergqvistjl on 2011-11-06
Well, I fixed it.  After ages of trying to tell the OS that I didn't want the Location of my mailbox to be /var/mail/username, I ended up just manually symlinking the Maildirs into /var/mail and it seems to be coping with that (and that it's now using MailDir as opposed to mbox) fine. Now I just need to get mail to stop copying read emails to an mbox file in my home dir whenever I quit mail...

---

