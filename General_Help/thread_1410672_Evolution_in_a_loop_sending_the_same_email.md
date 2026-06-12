---
title: "Evolution in a loop sending the same email"
date: 2010-02-19
forum: General Help
---

### Post by matthew.ball on 2010-02-19
Hey,

Basically, I think my Internet crashed while sending an email via Evolution and now whenever I open Evolution, or try and receive any new email it just sits there sending this email - it reaches 100% so I can only assume it has actually sent the email.

There's a button to "Cancel the current mail operation" though it doesn't appear to be doing anything; the email is still being "sent" each time.

This would be pretty tedious for the guy I sent the email to.

Has anyone had similar issues and knows of a fix? Any help is appreciated, thanks.

---

### Post by dcstar on 2010-02-19
> **matthew.ball said:**
> Hey,

Basically, I think my Internet crashed while sending an email via Evolution and now whenever I open Evolution, or try and receive any new email it just sits there sending this email - it reaches 100% so I can only assume it has actually sent the email.

There's a button to "Cancel the current mail operation" though it doesn't appear to be doing anything; the email is still being "sent" each time.

This would be pretty tedious for the guy I sent the email to.

Has anyone had similar issues and knows of a fix? Any help is appreciated, thanks.

Go into the .evolution/mail/local folder and delete the Outbox file.

---

### Post by matthew.ball on 2010-02-19
Yeah, I actually came to post that (thanks indus from #ubuntu on freenode).

However, it still thinks I want to send an email - just gives me an error saying:

```
Error while Sending message.

Can not get message: 14 from folder /home/chu/.evolution/mail/local/Outbox
  The folder appears to be irrecoverably corrupted.
```
I can't work out where this is coming from though.

---

