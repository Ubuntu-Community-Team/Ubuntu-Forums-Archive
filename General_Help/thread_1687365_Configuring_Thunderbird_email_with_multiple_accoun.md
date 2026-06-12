---
title: "Configuring Thunderbird email with multiple accounts."
date: 2011-02-13
forum: General Help
---

### Post by Bernie Gallagher on 2011-02-13
I currently use Evolution, which is the default email client that came with Ubuntu.  Now, Evolution is really easy to configure...type in the POP and SMTP servers for each account and it's off and running.  

Still, I'd like to switch to Mozilla Thunderbird.  

Now, all my email accounts require SMTP authentication, and so outgoing email from [email]me@a.com[/email] needs to go through a's SMTP server, while outgoing email from [email]me@b.com[/email] needs to go through b's SMTP server, etc., etc.

The trouble is that Thunderbird wants to send all outgoing mail through the same SMTP server.  Evolution can send outgoing email to the correct SMTP server.  Even Windoze Outlook and Live Mail clients can handle multiple SMTP servers easily.  Why not Thunderbird?

Has anyone else solved this problem with Thunderbird?

---

### Post by jwcalla on 2011-02-13
Edit -> Account Settings

In the left column select "Outgoing Server (SMTP)".

Click the "Add..." button and enter b.com's SMTP server details.

Then in the left column select [EMAIL="me@b.com"]me@b.com[/EMAIL]'s top-level account settings.  Near the bottom there is a pull-down option for "Outgoing Server (SMTP):".

voila!

---

### Post by Bernie Gallagher on 2011-02-13
Thanks, but I'll have to wait another day to try it...

---

### Post by fontman on 2011-02-20
Hi;

Will Thunderbird create "Profiles"?

I'd move to a [K]ubuntu client if I could find one that supports "Profiles" i.e. the ability to set up different sessions for work, pleasure, and other things. That way I don't have to keep changing my default e-mail address for different e-mails and I keep a clean and separate database of e-mails. I want to move away from Outlook.

---

### Post by CHRSB on 2011-02-21
> **fontman said:**
> Hi;

Will Thunderbird create "Profiles"?

I'd move to a [K]ubuntu client if I could find one that supports "Profiles" i.e. the ability to set up different sessions for work, pleasure, and other things. That way I don't have to keep changing my default e-mail address for different e-mails and I keep a clean and separate database of e-mails. I want to move away from Outlook.

First, some ettiqute, You want to post divergent questions that have no relation to the original post in a new thread. And also, try using search before asking a question. Laziness only makes you dumber. If you want to be dumb, buy an iPad.

Here is your answer:
open a terminal and type "thunderbird -p", no quotes.
[http://ubuntuforums.org/showthread.php?t=1608168](http://ubuntuforums.org/showthread.php?t=1608168)

Also, Thunderbird allows you to have several email accounts in one profile. I have three in mine.

---

### Post by fontman on 2011-02-22
> **CHRSB said:**
> First, some ettiqute, You want to post divergent questions that have no relation to the original post in a new thread. And also, try using search before asking a question. Laziness only makes you dumber. If you want to be dumb, buy an iPad.

Here is your answer:
open a terminal and type "thunderbird -p", no quotes.
[http://ubuntuforums.org/showthread.php?t=1608168](http://ubuntuforums.org/showthread.php?t=1608168)

Also, Thunderbird allows you to have several email accounts in one profile. I have three in mine.

Ouch!! Your response, while technically appreciated, seems rather arrogant. I did a search with the term profiles and was unable to find anything. Secondly, this is a topic about multiple accounts, so what's the big deal. 

Then you have the audacity to diverge the post yourself about stupid iPads, which I'd never buy, or anything from Apple.

BTW, it has to be a capital P, i.e. "thunderbird -P"

Thanks Anyway.

---

