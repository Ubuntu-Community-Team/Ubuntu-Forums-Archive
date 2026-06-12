---
title: "Mailman Setup"
date: 2011-03-01
forum: General Help
---

### Post by blharmon on 2011-03-01
Hi all, 
I have been fighting with installing mailman on a clean Ubuntu 10.10 box. I have tried following the documentation [_here_]("https://help.ubuntu.com/10.10/serverguide/C/mailman.html") 
and seem to be very close to getting this to work. I am using Postfix as well. 
I can create lists, as well as add members to the lists. Our mailman server sends messages out to these members notifying them that they are members. But my current issue is that if anyone sends to the list, they get a return message. Sending to the mail server from a gmail account gives the following:
The error that the other server returned was: 550 550 5.1.1 <mailman@lists.mydomain.org>: Recipient address rejected: User unknown in local recipient table (state 14) 

I'm a complete newb and am not sure where to go to troubleshoot this further. Can anyone offer some expertise? TIA

I tried sending an email via telnet to the mailman server, and after adding RCPT TO: [email]mailman@lists.domain.org[/email] I get the follwing back:
550 5.1.1 [email]itsupport@lists.domain.org[/email]: Recipient address rejected: user unknown in local recipient table.

---

