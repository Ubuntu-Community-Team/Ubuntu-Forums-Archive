---
title: "Apache Mail Bouncing"
date: 2011-07-19
forum: General Help
---

### Post by ubila on 2011-07-19
Hello, email from my client website is bouncing and im getting this error:
(i have edited out sensitive data)

Final-Recipient: RFC822; [email]clientemail@clienthostname.co.nz[/email]
Action: failed
Status: 5.1.1
Remote-MTA: DNS; mxa.company.co.nz
Diagnostic-Code: SMTP; 550 Rule imposed mailbox access for [email]clientemail@clienthostname.co.nz[/email] refused
Last-Attempt-Date: Mon, 18 Jul 2011 16:54:58 +1200

Anyone have any ideas why this is happening? My server can send mail to gmail without any troubles. It just seems trying to go to this clients mail server is get marked as spam?
Any suggestions on how to fix this?

Cheers

Edit: A bit more information


   ----- Transcript of session follows -----
... while talking to mxa.company.co.nz.:
>>> RCPT To:<clientemail@clienthostname.co.nz>
<<< 550 Rule imposed mailbox access for [email]clientemail@clienthostname.co.nz[/email] refused
550 5.1.1 <clientemail@clienthostname.co.nz>... User unknown
>>> DATA
<<< 503 Recipients required

TO ME that seems like the email address is invalid or does not exist! But the email address does exist!
I have even sent follow up emails to the client with replies from that email address...

Could it be > or because you were trying to reply to a message sent out under a falsified address 

---

### Post by SeijiSensei on 2011-07-20
Are you reponsible for the mail server that doesn't accept your messages, or is it someone at the client's site?  Maybe a conversation with that person will help.

There could be lots of reasons why they're refusing your mail.  Does your server have proper forward and reverse name resolution configured?  Is the sending server on a consumer connection with a dynamic address?  

There are so many reasons why people refuse mail these days that it's always best to speak with the mail admin at the remote site to work out a solution.

---

### Post by Habitual on 2011-07-21
maybe your sending IP is "dirty"?
You can check it's reputation at [http://www.spamcop.net/bl.shtml](http://www.spamcop.net/bl.shtml)

---

