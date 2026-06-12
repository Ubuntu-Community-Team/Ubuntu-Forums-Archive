---
title: "Postfix sent mail won't work properly"
date: 2011-01-07
forum: General Help
---

### Post by Mairmax on 2011-01-07
Hi

I have followed this( [PostfixBasicSetupHowto]("https://help.ubuntu.com/community/PostfixBasicSetupHowto")) to set up my postfix.

I've setted up thunderbird for sending and receiving messages.
When i sent a message, it must be sent to [email]user@mail.example.com[/email] instead off [email]user@example.com[/email].

Does somebody know where the problem is?

Thanks in advance

---

### Post by dcstar on 2011-01-07
> **Mairmax said:**
> Hi

I have followed this( [PostfixBasicSetupHowto]("https://help.ubuntu.com/community/PostfixBasicSetupHowto")) to set up my postfix.

I've setted up thunderbird for sending and receiving messages.
When i sent a message, it must be sent to [email]user@mail.example.com[/email] instead off [email]user@example.com[/email].

Does somebody know where the problem is?

Thanks in advance

What "problem", where are any error messages that describe a "problem"?

---

### Post by Mairmax on 2011-01-07
> **dcstar said:**
> What "problem", where are any error messages that describe a "problem"?
Ok if i mail to [email]user@example.com[/email] i get response from thunderbird:

```
An error occurred while sending mail. The mail server responded:  5.1.1 <user@example.com>: Recipient address rejected: example.com. Please check the message recipient user@example.com and try again
```

And when i mail to [email]user@mail.example.com[/email] the mail arrives in the inbox of [email]user@example.com[/email]

But i want to send mail's to [email]user@example.com[/email] and not to [email]user@mail.example.com[/email] .

---

### Post by efflandt on 2011-01-07
It is likely a DNS issue, but since you are not using a real domain, we would have no way of checking that.  In order to send mail to example.com, example.com either needs to be an A record in DNS, or needs to have an MX record pointing to an A name in DNS (not a cname).

And the smtp server receiving mail for example.com has to know to receive mail for that domain and not just its FQDN mail.example.com.  If you receive mail with postfix, what do you have for **mydestination**?  For example in an old box, I had for 2 different no-ip.com subdomains (now different) and a private de-local domain for a PC with hostname mainpc:

mydestination = localhost,realhost.no-ip.com,mail.realhost.no-ip.com,efflandt.no-ip.com,localhost.no-ip.com,localhost.de-local,mainpc.de-local

---

### Post by dcstar on 2011-01-07
> **efflandt said:**
> It is likely a DNS issue, **but since you are not using a real domain, we would have no way of checking that**.
........

Exactly, you cannot post bogus "examples" of things that require specific and exact data to diagnose and expect anything useful.

---

### Post by Mairmax on 2011-01-08
> **efflandt said:**
> 
what do you have for mydestination? 

Thanks! i've only added mail.example.org to mydestination and forgot to add example.org .

Thank You :P

---

