---
title: "hide ip address  - evolution mail?"
date: 2010-11-17
forum: General Help
---

### Post by sohlinux on 2010-11-17
Anyone know know how to hide an ip address while sending through evolution mail so the recipient cannot see the ip in the email header?

example below: I sent an email from evolution to my gmail account and I can see my real ip address in the mail header 80.x.x.x
 
Authentication-Results: mx.google.com; spf=neutral (google.com: is neither permitted nor denied by best guess record for domain of [email]email@email.com[/email]) smtp.mail=email@email.com Received: from([80.x.x.x] helo=[192.168.1.6])
 
I can hide my ip using a proxy but what are the other ways of doing this?

---

### Post by efflandt on 2010-11-17
That is simply part of smtp.  Any mail server reports the IP (and possibly DNS name) that it receives mail from.  That is often used to take action if it receives mail directly from some place it does not want to (known spammers, open relays, IP's that appear to be dynamic from the names they resolve to, etc.).

Although, some spam and worms add forged headers to make it tougher to follow the chain if the IP's are public and extends beyond where it really originated from.

---

### Post by sohlinux on 2010-11-17
> **efflandt said:**
> That is simply part of smtp.  Any mail server reports the IP (and possibly DNS name) that it receives mail from.  That is often used to take action if it receives mail directly from some place it does not want to (known spammers, open relays, IP's that appear to be dynamic from the names they resolve to, etc.).

Although, some spam and worms add forged headers to make it tougher to follow the chain if the IP's are public and extends beyond where it really originated from.

Thanks but I already know the ins and outs of why it sends the ip, I just want to know how to not send the ip (for security reasons).

if I send email from gmail via http it doesn't send my ip, strange it sends the ip via email clients like evolution. surely there is a simple way of hiding the ip.

---

### Post by trundlenut on 2010-11-17
more or less thinking out loud but when you send an email from gmail via http the first IP address will be the gmail server it is sent from where SMTP kicks in, when you send it via evolution the SMTP kicks in straightaway hence why your home IP is recorded.

What you therefore need is for evolution to send the email via gmail using http as the first step.  No idea if that is possible but could it be similar to outlook using http to connect to an exchange server?

---

### Post by sohlinux on 2010-11-17
> **trundlenut said:**
> more or less thinking out loud but when you send an email from gmail via http the first IP address will be the gmail server it is sent from where SMTP kicks in, when you send it via evolution the SMTP kicks in straightaway hence why your home IP is recorded.

What you therefore need is for evolution to send the email via gmail using http as the first step.  No idea if that is possible but could it be similar to outlook using http to connect to an exchange server?

good thinking.. yes maybe http or imap may do the trick, I will try it and post the results ;-)

---

