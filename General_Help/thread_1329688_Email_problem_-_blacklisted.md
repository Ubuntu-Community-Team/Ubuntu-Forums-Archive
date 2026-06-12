---
title: "Email problem - blacklisted ?"
date: 2009-11-17
forum: General Help
---

### Post by bramblewood on 2009-11-17
I cannot send email and get the following message
Error while Sending message.

RCPT TO <ebilling@bt.com> failed: 5.7.1 This message has been blocked because it is from a FortiGuard - AntiSpam black IP address.(connection black ip 87.115.157.23)

this seems to have started after I received two spam emails 

I am new to ubuntu can anybody help. Thanks

---

### Post by hal8000 on 2009-11-17
That IP address belongs to Plusnet, is that your ISP?

Can you send and receive email to an echo mailserver?

Send an email to

[email]echo@tu-berlin.de[/email]

You dont have to type a  subject or message, the echo mailserver will receive your mail and return it with full header info.

If this works ok, your mail is ok, there is a problem with either the recipient or perhaps you have some mail filter installed.

What program are you using to send/receive email and which ubuntu?

---

### Post by bramblewood on 2009-11-17
Thanks for your reply

same message if I try to send an email to that address.

Plus net is my ISP, my mail is sent from evolution on unbuntu 9.10

and goes via an any-mail.com POP server.

The message does appear to disappear from the sent items but is still there.

---

### Post by dcstar on 2009-11-17
> **bramblewood said:**
> Thanks for your reply

same message if I try to send an email to that address.

Plus net is my ISP, my mail is sent from evolution on unbuntu 9.10

and goes via an any-mail.com POP server.

The message does appear to disappear from the sent items but is still there.

This has nothing to do with Ubuntu, it is a combination of the IP address your ISP has assigned you and the anti-spam settings of the SMTP server you are using.

Complain to both of them.

---

### Post by bramblewood on 2009-11-19
Thanks for the post.

I think I have got around the problem by sending the mail out via a different sever.

---

