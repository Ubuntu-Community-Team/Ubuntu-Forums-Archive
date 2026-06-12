---
title: "Sendmail as SMTP-client w/o smarthost"
date: 2010-07-18
forum: General Help
---

### Post by inzpektor on 2010-07-18
Hi there.

My ISP (TDC/Yousee) decided to block their SMTP-gateways for anyone not using one of their own mail-addresses (blabla@tdc.dk, [email]blabla@post.tele.dk[/email], etc.).  After googling a bit, it seems that it nowadays is impossible to use free/open mail-hubs anywhere, and I'm left with having to set one up myself.

So, I started taking a look at sendmail as a mail-server, went on to postfix.  But then I noticed some SMTP-projects like esmtp, ssmtp, and nullmailer, but they all share the same restriction that they only work if you have access to a mail-hub/SMTP-gateway.

Just to get real basic functionality out of Postfix (SMTP_AUTH, TLS), you have to do a **lot** of configuration, including installing and configuring SASL.  I got as far as setting up TLS, but SMTP_AUTH kept failing with some SASL-error like "No mechanisms found", but I did have it configured for PAM.

As an experienced software-developer, I fail to understand why there's no mail-server with this basic functionality configured as default, and then perhaps without all the mail-filters, mapping tables etc. which you don't need if you're picking up your mail elsewhere.

Oh well, I finally went with sendmail as an SMTP-client on each machine.  It's easy to tell Evolution to use sendmail, and it seems to work, except for one peculiarity;

If I send a mail to "To: John Smith <john@smith.com>", everything works well and the mail is delivered.

However, if I send the same mail to "To: [email]john@smith.com[/email]", it never arrives at it's destination, but the mail.log doesn't show any problem.

Well, actually, the log does show a warning, but this warning is also shown in the previous case - which works;

> Jul 17 12:49:58 myhost sendmail[14232]: o6TEhr6e614242: Authentication-Warning: myhost.mydomain.com: myuser set sender to [email]john@smith.com[/email] using -f

Long story short: Why doesn't sendmail work with email-address-only To-fields?

---

