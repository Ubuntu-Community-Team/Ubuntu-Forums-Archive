---
title: "Microsoft Outlook Outbox Troubleshooting"
date: 2011-03-30
forum: General Help
---

### Post by theamazingbeat on 2011-03-30
Hello All,
 
Okay so hopefully this is just a simple setting that I can change but basically what is happening is my multiple mail accounts in outlook are going out my very first mailbox outbox (the very first one I created.) 
 
 
 
So lets say i have [EMAIL="test@domain.com"]test@domain.com[/EMAIL], as well [EMAIL="test2@domain2.com"]test2@domain2.com[/EMAIL], anytime I send an email, it sends it out of the only outbox, which is under [EMAIL="text@domain.com"]text@domain.com[/EMAIL]'s email.
 
 
[http://www.lookpic.com/c1/i2/3665/FZAzhm34.png/](http://www.lookpic.com/c1/i2/3665/FZAzhm34.png/)
 
So basically what I need help with is I need to establish an outbox for every single mailbox so when I send an email, it doesn't go out of the very top one, it goes out of the individual mailboxes outbox. So an outbox for every single account.... How do I do this? 
 
 
I am using Outlook 2010 Professional Plus
Win 7 Home Premium x64
 
when I was searching I found this:
 
[http://www.lookpic.com/c1/i2/3495/mQnRJkqY.png/](http://www.lookpic.com/c1/i2/3495/mQnRJkqY.png/)
 
 
 
So see this is what I need to change, each mailbox has to send out from its own individual mailbox, not just that one. 
 
Though, when I am looking at the account settings now, each one has a different outgoing server. Like the exachange has a server address, and the IMAP(Gmail), has smtp.google.com.....it is just that default setting that I need to turn off( or some other setting).
 
 
back to digging....

---

### Post by theamazingbeat on 2011-03-31
Found the issue, I wasn't doing anything wrong :P

My two email accounts were: Exchange & Gmail

The problem was Google was set to use IMAP and not POP3. For some reason (and I am tired so i really don't care nor want to look it up) when you have IMAP you use your default sender's outgoing server which then connects to your outgoing server, which is very stupid. Anyway, all POP3 email account have their own outbox associated with their own mailbox and outgoing server (how it is suppose to be). So just advise for anyone who has trouble, DO NOT USE IMAP! lol


But still struggling with one issue, my labels and folders I have set in Gmail are not showing up in Outlook....almost there


Persistence pays off.

---

